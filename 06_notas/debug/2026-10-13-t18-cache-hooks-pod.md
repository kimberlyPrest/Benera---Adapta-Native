# DEBUG T1.8 — Pod servindo hooks antigos após build verde (cache por arquivo)

**Data:** 2026-10-13 · **Task:** T1.8 · **Ambiente:** Skip 63138

## Debug Summary

**Task e problema:** após aplicar migração 0013 + hooks T1.8 com QA verde (v0.0.40→43), o runtime respondia com código ANTIGO: PATCH com status 'bloqueada' devolvia a mensagem da T1.7 ("Status inválido (use pendente ou concluida)") e a rota de handoff dava 404.

**Reprodução:** PATCH /backend/v1/tasks/{id} com status bloqueada → mensagem antiga; POST /backend/v1/projects/{key}/handoff → 404. Logs de requests confirmavam (status 404/400 com erro antigo). Logs de hooks vazios (0 itens).

**Causa raiz:** o recarregamento de hooks no pod é POR ARQUIVO — `skip_file_patch` (SEARCH/REPLACE) em arquivo existente pode não invalidar o cache, mesmo com build/QA verdes e versionHash novo. Evidência: o MESMO padrão se repetiu em 3 hooks (tarefas-atualizar, handoff-criar, projeto-transicao) e TODOS passaram a carregar após REESCRITA COMPLETA do arquivo (skip_file_write), não após patches.

**Correção:** reescrever o arquivo inteiro com skip_file_write (mesmo conteúdo lógico) + apply_changes. v0.0.44 (handoff OK), v0.0.45 (tarefas-atualizar OK), v0.0.46 (transição OK).

**Verificação automática:** v0.0.47 com todas as provas da T1.8 PASSOU (ver 05_entregas/t1.8-relatorio.md).

**Gate atual:** aguardando teste humano.

**Regra:** ao editar hook existente no Skip, preferir REESCRITA COMPLETA do arquivo; patch incremental pode não recarregar no pod. Se sintoma = "código antigo responde com QA verde", reescrever o arquivo e reaplicar antes de qualquer outra hipótese.

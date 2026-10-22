# DEBUG T1.10 — "não achei as notas" (nota criada via API não aparecia para o dono)

**Data:** 2026-10-22 · **Task:** T1.10 · **Reportado por:** champion (teste humano)

## Debug Summary

**Task e problema:** dono não encontrou as notas no Workspace; "criar nova tarefa deu certo".

**Reprodução e diagnóstico (e2e no navegador como u-consultor):**
1. Backend OK — API devolvia a nota "Contexto da negociação" na listagem (prova GREEN 1 já registrada).
2. Bundle antigo no navegador: a seção Workspace só chegou no bundle em v0.0.51; o dono estava com o bundle v0.0.49 cacheado (hard refresh resolve).
3. **Causa real de "não achei" mesmo com bundle novo:** a seção Workspace fica no FIM do cartão 360, DEPOIS de 27 tarefas de teste acumuladas — sem scroll, parecia que não existia. Prova: snapshot do navegador mostrou a seção com as 4 sub-abas e a nota visível após rolar.
4. Melhorias aplicadas (v0.0.52/53): espaçamento (mb-4) para separar visualmente a seção da lista de tarefas.

**Correção:** nenhum bug de código — era descobribilidade (seção abaixo de lista longa) + cache de bundle. Workspace provado e2e: sub-abas Notas/Comentários/Docs/Links/Entregas, nota visível, timeline com workspace_created/updated/archived/entrega_registered.

**Verificação automática:** v0.0.53 QA verde; e2e no navegador confirma a seção renderizada com dados.

**Gate atual:** aguardando reteste humano (hard refresh → abrir cartão → rolar até Workspace abaixo das tarefas).

**Resíduo relacionado:** as 27 tarefas de teste acumuladas em PROJ-F1-001 (T1.7–T1.9 + testes do dono) enterram a seção — faxina exige superusuário (regras nulas); recomendada antes do piloto.

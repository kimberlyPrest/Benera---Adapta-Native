# AP-2026-10-13-t18-cache-hooks — Cache de hooks no pod é POR ARQUIVO; reescrever, não patchar

**Origem:** T1.8 (Skip 63138) · **Data:** 2026-10-13

**Sinal:** QA verde (build/integrations ok, versionHash novo) mas o runtime respondia com o hook ANTIGO (mensagens de erro da versão anterior; rota nova 404).

**Aprendizado:** no Skip Cloud, o recarregamento de hooks no pod é POR ARQUIVO — `skip_file_patch` em arquivo existente pode não invalidar o cache. `skip_file_write` (reescrita completa) força o reload. Sintoma distintivo: resposta com mensagem de erro do código ANTIGO + QA verde.

**Regra aplicada:** reescrever hooks inteiros ao editar (tarefas-atualizar, handoff-criar, projeto-transicao — v0.0.44/45/46).

**Reutilizável:** qualquer edição de hook no Skip Cloud.

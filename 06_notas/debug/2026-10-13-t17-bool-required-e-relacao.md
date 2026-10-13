# DEBUG T1.7 — bool required rejeita false; relação p/ coleção da mesma migração

**Data:** 2026-10-13 · **Task:** T1.7 · **Ambiente:** Skip 63138

## Erro 1 — task_items com bool required
**Sinal:** POST de tarefa com checklist → 400 `{"concluido":{"code":"validation_required","message":"Cannot be blank."},"obrigatorio":{...}}`.
**Causa raiz:** no PocketBase, campo `bool` com `required: true` rejeita o valor `false` — a validação de obrigatório trata false como vazio.
**Fix:** migração 0012 remove `required` dos dois bools; a trava real é server-side no hook (conclusão exige obrigatórios concluídos). **Regra:** bool de negócio com valor false legítimo NUNCA leva `required`.

## Erro 2 — relation para coleção criada na mesma migração
**Sinal:** QA integrations: `fields: (1: (collectionId: The relation collection doesn't exist..)`.
**Causa raiz:** guardrail do Skip — relação com collectionId de coleção criada na MESMA migração não resolve por nome.
**Fix:** salvar a coleção alvo primeiro e usar `app.findCollectionByNameOrId('tasks').id` na relação. **Regra:** migração que cria duas coleções com referência cruzada resolve o id após o save (ou divide em duas migrações).

## Provas pós-fix (v0.0.37)
- GREEN 0/1/2/3 e RED 1/5 conforme relatório da T1.7.
- Resíduo: tarefas-lixo pré-fix (header salvo antes do erro nos itens) — remoção exige superusuário (regras nulas); faxina pendente de decisão.

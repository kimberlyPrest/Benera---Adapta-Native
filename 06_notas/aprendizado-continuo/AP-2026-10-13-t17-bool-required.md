# AP-2026-10-13-t17-bool-required — bool required rejeita false no PocketBase

**Origem:** T1.7 (Skip 63138) · **Data:** 2026-10-13

**Sinal:** POST de checklist → 400 "Cannot be blank" nos campos bool obrigatorio/concluido quando o valor era false.

**Aprendizado:** no PocketBase, campo bool com required=true rejeita o valor false (validação trata false como vazio). Bool de negócio com false legítimo NUNCA leva required — a trava real fica server-side no hook.

**Regra aplicada (migração 0012).**

**Reutilizável:** qualquer coleção PB com bool de negócio (ativo/inativo, obrigatório/não).

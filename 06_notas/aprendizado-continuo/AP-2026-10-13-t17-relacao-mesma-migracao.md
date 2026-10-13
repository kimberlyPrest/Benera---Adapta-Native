# AP-2026-10-13-t17-relacao-mesma-migracao — relação para coleção criada na mesma migração

**Origem:** T1.7 (Skip 63138) · **Data:** 2026-10-13

**Sinal:** QA integrations: "collectionId: The relation collection doesn't exist" na migração que criava tasks e task_items juntas.

**Aprendizado:** guardrail do Skip — relação com collectionId de coleção criada na MESMA migração não resolve por nome. Salvar a coleção alvo primeiro e usar app.findCollectionByNameOrId('alvo').id na relação (ou dividir em duas migrações).

**Regra aplicada (0010 reescrito).**

**Reutilizável:** qualquer migração com referência cruzada.

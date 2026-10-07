# AP-2026-10-07-1245 — Vínculo a projeto por chave exige validação de existência

**Origem:** T1.3 (Skip 63138) · **Data:** 2026-10-07

**Sinal:** o hook de concessão de vínculo (T1.2) aceitava qualquer `project_key` informado — um typo criava vínculo fantasma sem erro. Detectado na verificação de fechamento da T1.3, quando a coleção `projects` passou a existir.

**Aprendizado:** referência por chave textual (string de negócio) só é segura quando o endpoint valida a existência do registro referenciado. Ao introduzir a coleção referenciada, revisar hooks antigos que aceitam a chave como texto livre.

**Regra aplicada:** hook de vínculo agora valida `findFirstRecordByData('projects', 'project_key', ...)` antes de salvar; prova negativa 400 "Projeto não encontrado".

**Reutilizável:** qualquer task futura que receba chave textual de projeto/cliente (ex.: tarefas, bloqueios, handoffs em T1.7+).

# AP-2026-10-07-2031 — Campo de referência em texto livre gera duplicatas

**Origem:** erro reportado pelo champion na alocação (pós-T1.3) · **Data:** 2026-10-07

**Sinal:** alocação de consultor falhou; champion criou segundo projeto para o mesmo cliente (BENERA-KLABIN-OO1 vs PROJETO_KLABIN_001). Causa raiz: campo "Chave do projeto" em texto livre — chave digitada ≠ chave cadastrada; a validação de existência (v0.0.11) recusou, e o contorno natural do usuário foi cadastrar de novo.

**Aprendizado:** campo que referencia registro de catálogo deve ser SELECT vinculado à listagem, nunca texto livre — elimina a classe inteira de erro (typo + duplicata de cadastro). A validação server-side continua necessária (defesa em profundidade), mas a UI é a primeira barreira.

**Regra aplicada (v0.0.12):** aba "Alocar membro" usa select alimentado por GET /backend/v1/projects, exibindo "CHAVE — Nome".

**Reutilizável:** qualquer formulário futuro que referencie projeto/cliente/usuário (tarefas T1.7+, bloqueios, handoffs).

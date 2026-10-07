# Status

**Fase atual:** Fase 1 — Central operacional manual e baseline
**Estado:** 3 de 16 tasks concluídas (T1.1, T1.2 e T1.3, 19%); próxima elegível: T1.4
**Atualizado em:** 2026-10-07

## Ambiente e progresso

- Ambiente de implementação/homologação: Skip, projeto **63138**. Produção não autorizada nesta liberação.
- **T1.1 concluída (2026-10-05):** convite/ativação/login/perfis mínimos — migração 0002 (role, invites, fixture sintética, rotação da credencial exposta), hooks de convite, telas /convites e /ativar-acesso. Versões v0.0.2→v0.0.4, QA ok.
- **T1.2 concluída (2026-10-05):** autorização server-side por projeto, revogação e auditoria — migração 0003 (project_members, audit_log), 5 hooks (conceder/revogar/verificar acesso/listar membros/auditoria), senha fixture via segredo FIXTURE_TEST_PASSWORD. Versões v0.0.5→v0.0.7 (25123f4), QA ok.
- **Provas T1.2:** RED (403 sem vínculo, 403 auto-concessão, 401 sem auth), GREEN (201 concessão, 200 acesso com papel), REGRESSÃO (revogação efetiva → 403), AUDITORIA (member_granted/member_revoked/access_denied com ator+horário). CA-1-003..006 com evidência; nenhum segredo em código/log/evidência.
- **Teste humano:** aprovado pelo champion ao vivo (9 passos da matriz de papéis); erro de e-mail duplicado no convite confirmado como caminho de erro correto da SPEC.
- **Pendência registrada:** UI de gestão de membros (conceder/revogar pela tela) entra na T1.3 — decisão documentada de recorte (server-side na T1.2, UI na task de CRUD de projetos).
- **T1.3 concluída (2026-10-07):** modelo e CRUD mínimo de cliente, tipo de serviço e projeto — migração 0005 (clients/service_types/projects + fixture ACME-FIXTURE/PROJ-F1-001 + 4 tipos de serviço provisórios), 4 hooks server-side (clientes-criar, projetos-criar, catalogos-listar, usuarios-listar), tela /projetos com 3 abas (Novo projeto · Novo cliente · Alocar membro) e botão Projetos no Dashboard para admin e líder. Versões v0.0.8→v0.0.11, QA ok. Matriz validada pelo champion (05/10): admin e líder cadastram; consultor e revisor negados (403). Provas: campos obrigatórios 400 com detalhe por campo, duplicados 400, fixture persistida, vínculo fantasma 400 (higiene herdada da T1.2), deleção física não exposta. Teste humano aprovado pelo champion (cadastro e alocação pela tela, incluindo projeto real PROJETO_KLABIN_001). Pendência da T1.2 fechada. CA-1-007 com evidência.
- T1.4 e demais tasks mantêm suas dependências.

## Próxima ação

Champion solicita a próxima task quando quiser (T1.4 é a elegível por dependência).

# Status

**Fase atual:** Fase 1 — Central operacional manual e baseline
**Estado:** 2 de 16 tasks concluídas (T1.1 e T1.2, 13%); próxima elegível: T1.3
**Atualizado em:** 2026-10-05

## Ambiente e progresso

- Ambiente de implementação/homologação: Skip, projeto **63138**. Produção não autorizada nesta liberação.
- **T1.1 concluída (2026-10-05):** convite/ativação/login/perfis mínimos — migração 0002 (role, invites, fixture sintética, rotação da credencial exposta), hooks de convite, telas /convites e /ativar-acesso. Versões v0.0.2→v0.0.4, QA ok.
- **T1.2 concluída (2026-10-05):** autorização server-side por projeto, revogação e auditoria — migração 0003 (project_members, audit_log), 5 hooks (conceder/revogar/verificar acesso/listar membros/auditoria), senha fixture via segredo FIXTURE_TEST_PASSWORD. Versões v0.0.5→v0.0.7 (25123f4), QA ok.
- **Provas T1.2:** RED (403 sem vínculo, 403 auto-concessão, 401 sem auth), GREEN (201 concessão, 200 acesso com papel), REGRESSÃO (revogação efetiva → 403), AUDITORIA (member_granted/member_revoked/access_denied com ator+horário). CA-1-003..006 com evidência; nenhum segredo em código/log/evidência.
- **Teste humano:** aprovado pelo champion ao vivo (9 passos da matriz de papéis); erro de e-mail duplicado no convite confirmado como caminho de erro correto da SPEC.
- **Pendência registrada:** UI de gestão de membros (conceder/revogar pela tela) entra na T1.3 — decisão documentada de recorte (server-side na T1.2, UI na task de CRUD de projetos).
- T1.3 e demais tasks mantêm suas dependências.

## Próxima ação

Champion solicita a próxima task quando quiser (T1.3 é a elegível por dependência).
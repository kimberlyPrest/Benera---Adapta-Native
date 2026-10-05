# Status

**Fase atual:** Fase 1 — Central operacional manual e baseline
**Estado:** 1 de 16 tasks concluída (T1.1, 06%); próxima elegível: T1.2
**Atualizado em:** 2026-10-05

## Ambiente e progresso

- Ambiente de implementação/homologação: Skip, projeto **63138**. Produção não autorizada nesta liberação.
- **T1.1 concluída (2026-10-05):** convite/ativação/login/perfis mínimos implementados no Skip 63138 — migração 0002 (campo role, coleção invites, fixture sintética, rotação da credencial exposta), hooks de convite (criar/listar/aceitar), telas /convites e /ativar-acesso, Dashboard com papel real, dica de credencial demo removida do login. Versões v0.0.2→v0.0.4 (9727684), QA ok.
- **Segurança:** cadastro público fechado (só superusuário/convite), autoatribuição de papel bloqueada server-side, token de convite hasheado com expiração 48h e uso único. Provas negativas registradas no relatório `artifacts/benera-p1/t1.1-relatorio.md` (anônimo 403, rotas de convite 401, token inválido 400, credencial exposta invalidada).
- **Teste humano:** aprovado pelo champion em 2026-10-05 09:4x — reset de senha e login funcionando após correção dos templates de e-mail (host do preview literal durante homologação; dívida registrada para reverter quando a produção for publicada).
- **CA-1-002 NÃO declarado atendido:** matriz inicial de papéis (admin configura; consultor não; líder/revisor deny-default) aguarda validação operacional da Benera.
- T1.2 e demais tasks mantêm suas dependências; esta conclusão não declara seus critérios atendidos.

## Próxima ação

Champion solicita a próxima task quando quiser (T1.2 é a elegível por dependência). Validar operacionalmente a matriz de papéis segue pendente da Benera.
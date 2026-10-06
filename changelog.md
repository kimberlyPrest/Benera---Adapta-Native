# Changelog

## 2026-10-05
- Task T1.2 concluída: autorização server-side por projeto, revogação e auditoria no Skip 63138 (v0.0.5→v0.0.7, QA ok). Coleções project_members/audit_log com regras nulas (só superusuário via API), 5 hooks server-side, senha fixture via segredo FIXTURE_TEST_PASSWORD (nunca em código/log). Provas RED/GREEN/REGRESSÃO/AUDITORIA aprovadas e validadas ao vivo pelo champion (9 passos da matriz). CA-1-003..006 com evidência. Relatório: artifacts/benera-p1/t1.2-relatorio.md.
- Decisão de recorte documentada: UI de gestão de membros (conceder/revogar pela tela) entra na T1.3 — T1.2 fecha com server-side verificado; champion confirmou a prática de corrigir e documentar por task, sem acumular ajustes para o final.
- Task T1.1 concluída: convite/ativação/login/perfis mínimos (v0.0.2→v0.0.4, QA ok). Migração 0002 (role + invites + fixture sintética + rotação da credencial exposta), hooks de convite, telas /convites e /ativar-acesso, papel real no Dashboard, dica de credencial demo removida. Teste humano aprovado pelo champion (reset + login). CA-1-001 com evidência; CA-1-002 validado com o teste da matriz ao vivo.
- DEBUG T1.1: link de redefinição apontava para produção não publicada (404) — causa raiz: passada Go da plataforma resolve {RESET_URL} DEPOIS do hook de tenant; corrigido reescrevendo os templates de e-mail com host do preview literal + {TOKEN} nativo. Dívida: reverter templates quando a produção for publicada. Detalhes em 06_notas/debug/.

## 2026-10-02
- Handoff inicial da Fase 1 aprovado e publicado (7 SPECs, 42 critérios de aceite, 16 tasks em 11 levas).
- Escopo definitivo incluído na raiz como `02-Escopo-Definitivo.md`.
- Registrado o levantamento compartilhado com Kim: carcaça de autenticação existente no Skip 63138; convite e papéis ainda pendentes. Não equivale ao aceite da T1.1.
- Kim autorizou implementar a T1.1 no ambiente Skip 63138, preservando seus critérios e o gate de validação da matriz/fixture.
- Cadastro público e credencial de demonstração exposta registrados como impedimentos de homologação, a corrigir sem publicar valores de segredos.
- Autorização, limites e roteiro de prova em `06_notas/2026-10-02-autorizacao-t1-1.md`. Nenhum código, segredo ou configuração do Skip foi alterado por esta publicação documental.
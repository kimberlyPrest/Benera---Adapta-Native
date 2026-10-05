# Changelog

## 2026-10-05
- Task T1.1 concluída: convite/ativação/login/perfis mínimos no Skip 63138 (v0.0.2→v0.0.4, QA ok). Migração 0002 (role + invites + fixture sintética + rotação da credencial exposta), hooks de convite, telas /convites e /ativar-acesso, papel real no Dashboard, dica de credencial demo removida. Cadastro público fechado e autoatribuição de papel bloqueada server-side. Teste humano aprovado pelo champion (reset + login). CA-1-001 com evidência; CA-1-002 aguarda validação operacional da matriz. Relatório: artifacts/benera-p1/t1.1-relatorio.md.
- DEBUG T1.1: link de redefinição apontava para produção não publicada (404) — causa raiz: passada Go da plataforma resolve {RESET_URL} DEPOIS do hook de tenant; corrigido reescrevendo os templates de e-mail com host do preview literal + {TOKEN} nativo. Dívida: reverter templates quando a produção for publicada. Detalhes em 06_notas/debug/.

## 2026-10-02
- Handoff inicial da Fase 1 aprovado e publicado (7 SPECs, 42 critérios de aceite, 16 tasks em 11 levas).
- Escopo definitivo incluído na raiz como `02-Escopo-Definitivo.md`.
- Registrado o levantamento compartilhado com Kim: carcaça de autenticação existente no Skip 63138; convite e papéis ainda pendentes. Não equivale ao aceite da T1.1.
- Kim autorizou implementar a T1.1 no ambiente Skip 63138, preservando seus critérios e o gate de validação da matriz/fixture.
- Cadastro público e credencial de demonstração exposta registrados como impedimentos de homologação, a corrigir sem publicar valores de segredos.
- Autorização, limites e roteiro de prova em `06_notas/2026-10-02-autorizacao-t1-1.md`. Nenhum código, segredo ou configuração do Skip foi alterado por esta publicação documental.
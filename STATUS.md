# Status

**Fase atual:** Fase 2 — Integração SharePoint
**Estado:** T2.1 CONCLUÍDA (escrita liberada e provada); T2.2 é a próxima elegível (navegador de arquivos server-side)
**Atualizado em:** 2026-10-26

## Fase 1 — ENCERRADA (2026-10-26)

16/16 tasks · 42/42 critérios · 7/7 SPECs · aceite humano registrado. Detalhes em `04_fase-atual/`.

## Fase 2 — em andamento

- **T2.1 concluída (2026-10-26, CA-2-001..004):** re-consentimento Sites.ReadWrite.All via device flow (dono executou; evidência: tela de confirmação Microsoft capturada). Provas: RED confirmado (criar pasta sem escrita → 403, ponto de partida documentado); GREEN — pasta `_TESTE_FASE2` criada (201), upload `t21-prova-escrita.txt` (201, webUrl no site BENERACORP), download com conteúdo íntegro byte a byte (True), listagem confirmando o arquivo; REGRESSÃO — OneDrive pessoal 200 e biblioteca CONSULTORIA 200 (10 itens listados). Token salvo em `scripts/.benera_token.json` (chmod 600, fora do repo, com refresh token p/ renovação automática). Script: `scripts/t21-consent-escrita.py`.
- T2.2 (navegador de arquivos server-side, CA-2-005..008) é a próxima; T2.3 vínculo, T2.4 upload auditado, T2.5 roteiro + dossiê.

## Dívidas rastreadas (da Fase 1)

- Templates de e-mail com host do preview — reverter na publicação em produção.
- Edição concorrente de workspace = última escrita vence.
- Duplicado BENERA-KLABIN-OO1/PROJETO_KLABIN_001 inativável pela tela.
- Ids de itens de checklist não expostos na listagem de tarefas.

## Próxima ação

Champion autoriza a T2.2 — navegador de arquivos do SharePoint na UI (hook server-side com o token do backend, escopo herdado da carteira, auditoria de acesso).

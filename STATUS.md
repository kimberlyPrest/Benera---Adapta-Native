# Status

**Fase atual:** Fase 2 — Integração SharePoint
**Estado:** T2.2 CONCLUÍDA (CA-2-005..008 fechados); T2.3 é a próxima elegível (vínculo workspace ↔ SharePoint)
**Atualizado em:** 2026-10-26

## Fase 1 — ENCERRADA (2026-10-26)

16/16 tasks · 42/42 critérios · 7/7 SPECs · aceite humano registrado. Detalhes em `04_fase-atual/`.

## Fase 2 — em andamento

- **T2.1 concluída (CA-2-001..004):** escrita no SharePoint provada (RED 403 → GREEN íntegro → regressão limpa); device flow executado pelo dono.
- **T2.2 concluída (2026-10-26, CA-2-005..008):** navegador de arquivos do SharePoint. Teste humano aprovado (dono: "Aprovar T2.2 e fechar CA-2-005..008"); revalidação do zero na v0.0.70 — GREEN raiz 21 itens / CONSULTORIA 28 / _TESTE_FASE2 com arquivo da T2.1 / busca com caminho completo; sanitização ../x e /abs → 400 auditado; CA-2-008 zero token nas respostas; auditoria 12 sharepoint_consulta + 8 access_denied; 404 limpo; regressão Fase 1 200; e2e visual com screenshot (navegação CONSULTORIA). Pendência declarada: fixture u-revisor 401 — RED sem vínculo provado por via indireta (access_denied na auditoria, mesmo caminho de código da T1.11).
- T2.3 (vínculo workspace ↔ SharePoint, CA-2-009..012) é a próxima; T2.4 upload auditado, T2.5 roteiro + dossiê.

## Dívidas rastreadas

- Templates de e-mail com host do preview — reverter na publicação em produção (F1).
- Edição concorrente de workspace = última escrita vence (F1).
- Duplicado BENERA-KLABIN-OO1/PROJETO_KLABIN_001 inativável pela tela (F1).
- Ids de itens de checklist não expostos na listagem de tarefas (F1).
- Credencial da fixture u-revisor@example.invalid inválida (401) — prova direta do RED sem vínculo pendente (F2).

## Próxima ação

Champion solicita a T2.3 quando quiser — vínculo documento workspace ↔ arquivo SharePoint: no cartão do projeto, documento pendente ganha "Vincular do SharePoint" (escolhe o arquivo no navegador da T2.2, hook resolve o link permanente, badge ORIGEM PENDENTE fecha sozinho, auditado; fallback manual preservado).

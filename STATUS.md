# Status

**Fase atual:** Fase 2 — Integração SharePoint
**Estado:** T2.3 implementada (vínculo workspace ↔ SharePoint, v0.0.76) — aguardando teste humano; T2.4 é a próxima
**Atualizado em:** 2026-10-26

## Fase 1 — ENCERRADA (2026-10-26)

16/16 tasks · 42/42 critérios · 7/7 SPECs · aceite humano registrado. Detalhes em `04_fase-atual/`.

## Fase 2 — em andamento

- **T2.1 concluída (CA-2-001..004):** escrita no SharePoint provada; device flow executado pelo dono.
- **T2.2 concluída (CA-2-005..008):** navegador de arquivos server-side; teste humano aprovado 26/10.
- **T2.2b concluída (CA-2-009..012, v0.0.74):** escopo por projeto — regra do dono (Maestro 100%, consultor só pastas dos projetos alocados); teste humano aprovado 26/10 ("Aprovar T2.2b e seguir para a T2.3").
- **T2.3 implementada (CA-2-013..016, v0.0.76) — AGUARDANDO TESTE HUMANO:** vínculo documento workspace ↔ arquivo SharePoint. Migração 0021 (sp_caminho/sp_weburl + audit workspace_vinculado); hook POST /backend/v1/workspace/{id}/vincular-sharepoint (escopo T2.2b aplicado: consultor só dentro da pasta do projeto, 403 auditado fora; 404 limpo; item já vinculado → 400; resolve no Graph e grava webUrl em origem_url, fechando o badge ORIGEM PENDENTE); listagem do workspace devolve sp_caminho/sp_weburl; UI: botão "Vincular do SharePoint" no badge pendente e no modo edição, picker inline com menu de escopo (T2.2b), navegação, busca e seleção. Provas: RED 403/400/404 · GREEN vínculo consultor (origem completada, auditado) · re-vínculo 400 · regressão 200. E2e visual pela UI como consultor. Itens de teste inativados (histórico preservado).
- T2.4 (upload auditado) é a próxima; T2.5 roteiro + dossiê + aceite.

## Dívidas rastreadas

- Templates de e-mail com host do preview — reverter na publicação em produção (F1).
- Edição concorrente de workspace = última escrita vence (F1).
- Duplicado BENERA-KLABIN-OO1/PROJETO_KLABIN_001 inativável pela tela (F1).
- Ids de itens de checklist não expostos na listagem de tarefas (F1).
- Credencial da fixture u-revisor@example.invalid inválida (401) — prova direta do RED sem vínculo pendente (F2).
- Projetos sem sp_folder: consultor alocado recebe 403 "nenhum projeto seu tem pasta mapeada" — mapear pasta ao criar/alocar projeto (F2).
- Picker do SharePoint vive no modo edição do item (botão do badge abre edição + picker) — unificar num drawer próprio em rodada de UX (F2).

## Próxima ação

Dono testa no cartão do projeto: aba Docs/Links → documento pendente → "Vincular do SharePoint" → escolher arquivo → Vincular (badge ORIGEM PENDENTE fecha, origem = link do SharePoint). Depois T2.4 — upload auditado.

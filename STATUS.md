# Status

**Fase atual:** Fase 2 — Integração SharePoint
**Estado:** T2.2 implementada e provada (v0.0.70, QA ok) — AGUARDANDO TESTE HUMANO; T2.3 é a próxima elegível
**Atualizado em:** 2026-10-26

## Fase 1 — ENCERRADA (2026-10-26)

16/16 tasks · 42/42 critérios · 7/7 SPECs · aceite humano registrado. Detalhes em `04_fase-atual/`.

## Fase 2 — em andamento

- **T2.1 concluída (CA-2-001..004):** escrita no SharePoint provada (RED 403 → GREEN íntegro → regressão limpa); device flow executado pelo dono.
- **T2.2 implementada (v0.0.64→70, QA ok) — AGUARDANDO TESTE HUMANO:** navegador de arquivos do SharePoint (CA-2-005..008). Migração 0019 (coleção ms_tokens com regras nulas + audit sharepoint_consulta); secret SHAREPOINT_REFRESH_TOKEN; hook sharepoint-listar (server-side, token nunca no front; renovação automática via secret + rotação persistida em ms_tokens; sanitização de caminho; busca via Graph search com caminho completo; 404 limpo; erro do Graph como aviso visível sem stack); tela /sharepoint (breadcrumb, lista com ícones, busca, link abrir no SharePoint) + rota no App. Provas: RED — consultor com vínculo 200 (régua validada), sanitização ../x e /abs → 400 auditado; GREEN — raiz da biblioteca 21 itens (pastas reais 00-ANETECLIN, 00-STARIAN, CONSULTORIA, _TESTE_FASE2...), CONSULTORIA 28 itens, _TESTE_FASE2 com o arquivo da T2.1 (117B, webUrl), busca "t21-prova" → 2 resultados com caminho completo; CA-2-008 — varredura de 4 respostas: zero token; auditoria — 5 sharepoint_consulta + 6 access_denied; 404 em pasta inexistente; REGRESSÃO — painel/exportar/fila/previews 200. E2E visual: login → /sharepoint com as 21 pastas reais → navegação para CONSULTORIA (28 itens) → screenshot como evidência.
- **Debugs registrados:** (1) scoping JSVM — top-level declarations não visíveis no callback (v0.0.64→65, lógica inline); (2) res.body é bytes no JSVM — JSON.parse(res.body) lança SyntaxError; usar res.json (v0.0.66→69; o patch da 66 aplicou só 1 de 2 blocos — o OAuth continuou com JSON.parse até a 69); (3) apply com buildRun null não commita — hook debug sumiu da árvore e precisou ser reescrito (v0.0.67→68); (4) badge da tela com versão antiga corrigido (v0.0.70).
- **Pendência de evidência (declarada):** login da fixture u-revisor@example.invalid falha (401) em 3 tentativas — o RED "sem vínculo" está provado por via indireta (6 access_denied na auditoria, mesmo caminho de código validado na T1.11); revisor não é usado desde a T1.11. Corrigir credencial da fixture em task futura se o dono quiser a prova direta.

## Dívidas rastreadas (da Fase 1)

- Templates de e-mail com host do preview — reverter na publicação em produção.
- Edição concorrente de workspace = última escrita vence.
- Duplicado BENERA-KLABIN-OO1/PROJETO_KLABIN_001 inativável pela tela.
- Ids de itens de checklist não expostos na listagem de tarefas.
- **NOVA:** credencial da fixture u-revisor@example.invalid inválida (401) — prova direta do RED sem vínculo pendente.

## Próxima ação

Champion testa a T2.2 pela UI (/sharepoint: navegar, buscar, abrir no SharePoint) e aprova; depois T2.3 (vínculo workspace ↔ SharePoint — fecha o badge ORIGEM PENDENTE escolhendo o arquivo no navegador).

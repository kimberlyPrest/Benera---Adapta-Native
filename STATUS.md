# Status

**Fase atual:** Fase 2 — Integração SharePoint
**Estado:** T2.2b implementada (escopo por projeto, v0.0.74) — aguardando teste humano; T2.3 é a próxima
**Atualizado em:** 2026-10-26

## Fase 1 — ENCERRADA (2026-10-26)

16/16 tasks · 42/42 critérios · 7/7 SPECs · aceite humano registrado. Detalhes em `04_fase-atual/`.

## Fase 2 — em andamento

- **T2.1 concluída (CA-2-001..004):** escrita no SharePoint provada (RED 403 → GREEN íntegro → regressão limpa); device flow executado pelo dono.
- **T2.2 concluída (CA-2-005..008):** navegador de arquivos server-side; teste humano aprovado 26/10.
- **T2.2b implementada (26/10, v0.0.74) — AGUARDANDO TESTE HUMANO:** regra do dono — Maestro/admin 100% da biblioteca; consultor/revisor SÓ as pastas dos projetos alocados. Migração 0020 (projects.sp_folder); PATCH de projeto aceita sp_folder (auditado, inválido → 400); hook com escopo (raiz do consultor = menu dos projetos, 0 itens — anti-enumeração; caminho fora do escopo → 403 auditado; busca filtrada com caminho derivado do webUrl, pois o Graph search não devolve parentReference.path); UI com seletor "Seus projetos no SharePoint". Mapeamentos reais: STARIAN-001 → 00 - STARIAN; PILOTO-F1-001 → _TESTE_FASE2. Provas: RED 403 (CONTRATOS, 00 - ANETECLIN) · GREEN dentro do escopo (14 itens, subpastas, busca filtrada) · admin inalterado · zero token · regressão 200. E2e visual como consultor (screenshot). Pendência declarada: fixture u-revisor 401 (RED sem vínculo por via indireta — access_denied na auditoria).
- T2.3 (vínculo workspace ↔ SharePoint, CA-2-009..012) é a próxima; T2.4 upload auditado, T2.5 roteiro + dossiê.

## Dívidas rastreadas

- Templates de e-mail com host do preview — reverter na publicação em produção (F1).
- Edição concorrente de workspace = última escrita vence (F1).
- Duplicado BENERA-KLABIN-OO1/PROJETO_KLABIN_001 inativável pela tela (F1).
- Ids de itens de checklist não expostos na listagem de tarefas (F1).
- Credencial da fixture u-revisor@example.invalid inválida (401) — prova direta do RED sem vínculo pendente (F2).
- Projetos sem sp_folder: consultor alocado recebe 403 "nenhum projeto seu tem pasta mapeada" — mapear pasta ao criar/alocar projeto (F2).

## Próxima ação

Dono testa a tela /sharepoint como consultor (deve ver só _TESTE_FASE2 e 00 - STARIAN) e aprova a T2.2b; depois T2.3 — vínculo documento workspace ↔ arquivo SharePoint, já nascendo dentro do escopo.

# Status

**Fase atual:** Fase 2 — Integração SharePoint
**Estado:** T2.4 implementada (upload auditado, v0.0.80) — aguardando teste humano; T2.5 fecha a fase
**Atualizado em:** 2026-10-26

## Fase 2 — progresso

- T2.1 ✓ (CA-2-001..004) · T2.2 ✓ (CA-2-005..008) · T2.2b ✓ (CA-2-009..012) · T2.3 ✓ (CA-2-013..016) · **T2.4 implementada (CA-2-017..020, v0.0.80) — AGUARDANDO TESTE HUMANO** · T2.5 (roteiro + dossiê + aceite) pendente.
- **T2.4 (v0.0.80):** upload auditado com a regra do dono — conexão/configuração do SharePoint é SEMPRE do admin; o consultor nunca escolhe destino: o arquivo vai para a pasta mapeada no projeto (sp_folder), o hook nem aceita parâmetro de destino. Fluxo: POST sharepoint-upload (valida vínculo + sp_folder + nome sanitizado + ≤10 MB; cria item pendente; abre upload session no Graph) → navegador faz PUT direto com Content-Range (binário nunca passa pelo servidor) → POST finalizar (confirma no Graph, grava sp_caminho/sp_weburl/origem_url, fecha o badge, audita workspace_upload com ator/caminho/tamanho). Conflito de nome → 409 tratado com aviso; arquivo não enviado → item pendente permanece para nova tentativa.
- Provas: RED 403 (sem pasta mapeada) · 400 (nome com /, tamanho 0, 11 MB) · GREEN upload completo (201, 44 B íntegros) · zero token · regressão 200. E2e visual do formulário.

## Lições técnicas (T2.4)

- Hook novo em arquivo novo não registrou na v0.0.78 (rota 404 com QA verde) — reescrita do arquivo forçou re-registro na v0.0.79 (mesmo padrão do cache da T1.8).
- Upload session do Graph EXIGE Content-Range mesmo para arquivo único (PUT sem o header → 400 invalidRequest).
- UI: bloco de upload dentro do fragmento do tipo documento no formulário de novo item.

## Dívidas rastreadas

- Templates de e-mail com host do preview (F1) · edição concorrente = última escrita (F1) · duplicado KLABIN inativável pela tela (F1) · ids de checklist não expostos (F1).
- Fixture u-revisor 401 — RED sem vínculo por via indireta (F2).
- Projetos sem sp_folder → consultor recebe 403 orientado a pedir mapeamento (F2).
- Picker do SharePoint vive no modo edição do item — unificar em drawer próprio em rodada de UX (F2).

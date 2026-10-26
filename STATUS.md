# Status

**Fase atual:** Fase 1 — Central operacional manual e baseline
**Estado:** 14 de 16 tasks implementadas (T1.1–T1.14, 88%); T1.14 aguarda teste humano; próxima elegível: T1.15 (preparação do piloto, SPEC-1-007)
**Atualizado em:** 2026-10-26

## Ambiente e progresso

- Ambiente de implementação/homologação: Skip, projeto **63138**. Produção não autorizada nesta liberação.
- **T1.1–T1.13 concluídas (2026-10-05 a 2026-10-26, v0.0.2→62):** histórico completo por task no changelog — convite/login/perfis (0002), autorização server-side (0003), CRUD cliente/projeto (0005), cartão 360/filtros/inativação (0006), esteira configurável com versão/rollback (0007/0008), Kanban/transições (0009), tarefas/checklists (0010/0011/0012), bloqueio/retorno/handoff idempotente (0013), fila individual, workspace interno (0014), permissões herdadas + fallback manual (0015), faxina das tarefas de teste (0016), painel operacional (0016→58), touch time/espera/ciclo/baseline (0017, 59→62).
- **T1.14 implementada (2026-10-26, v0.0.63, QA ok) — AGUARDANDO TESTE HUMANO:** exportação sanitizada, autorização de exportar e auditoria (CA-1-034/035/036). Migração 0018 (painel_config com regras nulas, seed corte_eventos=500; audit estendido com painel_consulta e export_realizada). Hook exportar-dados (GET /backend/v1/exportar?formato=csv|json + filtros do painel): só admin/líder (consultor/revisor 403 AUDITADO); sanitização server-side de TODA célula de texto iniciada com = + - @ tab CR → apóstrofo ANTES da entrega; corpo SEM timestamp (determinismo — gerado_em vai só no envelope e na auditoria); auditado export_realizada com ator/formato/filtros/linhas; arquivo montado no navegador só após 200 completo. Hook painel-config (GET/PUT, só admin, limites 50–5000, config_changed com antes→depois, REVERSÍVEL). Painel reescrito: CADA CONSULTA auditada como painel_consulta (CA-1-036) e corte da amostra lido da painel_config (mudar config muda o relatório de verdade). UI: botões Exportar CSV/JSON (só admin/líder) com hash SHA-256 exibido pós-download, config do corte visível para admin. Provas: RED 403/400; GREEN CSV (11 linhas, seções METADADO/BASELINE/PROJETO/TOTAL, 5 limitações) e JSON; sanitização provada com projeto sintético "=1+1 teste sanitizacao" → célula '=1+1 no CSV e no JSON (inerte antes da entrega); config_changed 500→300→500 auditado e reversível (baseline refletiu o corte em cada passo); consultor PUT 403; valor 10 → 400; determinismo (linhas PROJETO idênticas em 2 exportações, timestamp só no envelope); filtro sem dados 200/0 linhas; limpeza (sintético inativado por key, painel ativo sem ele); regressão geral (PROJ-F1-001 20.4d, fila, previews 200). E2E visual: login pela UI → dashboard → /painel.
- T1.15 e T1.16 mantêm suas dependências (T1.15 depende de T1.14 concluída).

## Próxima ação

Champion testa a T1.14 pela UI (/painel → Exportar CSV/JSON) e aprova; depois T1.15 (fixture + projeto-piloto, abre a SPEC-1-007).

# Status

**Fase atual:** Fase 1 — Central operacional manual e baseline
**Estado:** 13 de 16 tasks concluídas (T1.1–T1.13, 81%); próxima elegível: T1.14 (fecha a SPEC-1-006)
**Atualizado em:** 2026-10-26

## Ambiente e progresso

- Ambiente de implementação/homologação: Skip, projeto **63138**. Produção não autorizada nesta liberação.
- **T1.1–T1.12 concluídas (2026-10-05 a 2026-10-23, v0.0.2→58):** histórico completo por task no changelog e nas versões anteriores deste arquivo — convite/login/perfis (0002), autorização server-side (0003), CRUD cliente/projeto (0005), cartão 360/filtros/inativação (0006), esteira configurável com versão/rollback (0007/0008), Kanban/transições (0009), tarefas/checklists (0010/0011/0012), bloqueio/retorno/handoff idempotente (0013), fila individual, workspace interno (0014), permissões herdadas + fallback manual (0015), faxina das tarefas de teste (0016), painel operacional com agregados filtráveis.
- **T1.13 concluída (2026-10-26):** touch time, espera, ciclo e baseline (CA-1-032/033/037). Migração 0017 (coleção apontamentos, regras nulas, APPEND-ONLY: não se edita nem se apaga — correção é novo apontamento; inativação preserva registro e evento; resposta ao risco da SPEC "métrica gameável": registro manual separado dos eventos automáticos e auditado). Hooks apontamento-criar/listar/inativar (escopo por vínculo; minutos 1–600, motivo obrigatório; etapa default = etapa atual). Métricas no hook do painel: ciclo (dias corridos, criação → último evento de auditoria, BRT), touch (soma de minutos de apontamentos ATIVOS), espera (ciclo − touch, piso 0), incompleto (sem apontamento → flag, dado ausente ≠ zero). BASELINE como objeto calculado: período (2026-10-06 → hoje), relógio (dias corridos, BRT), amostra (projetos · apontamentos · eventos com corte 500 declarado), 5 limitações FIXAS incluindo nota anti-ganho "baseline é o PRIMEIRO ciclo — não é ganho; não há comparação pós-baseline (CA-1-037)" no CONTRATO DA API. UI: seção Tempo no cartão 360 (form minutos+motivo, lista, inativar) + seção Tempo e baseline no /painel. Provas: RED revisor 403 auditado; apontamento inválido 400; touch/espera distintas (ciclo 20.4d, touch 0.1d, espera 20.3d); incompleto em projetos sem apontamento; determinismo; append-only (PATCH sem inativar 400; inativação preserva evento; 8 eventos na auditoria); limpeza (touch 0, dado volta a INCOMPLETO); regressão geral. **Bug pego e corrigido:** parse de data com sufixo ZZ zerava o ciclo (v0.0.62 — ciclo real provado). E2E pela UI: apontar 45 min no cartão → touch 2h→2.8h → painel ciclo 20.4/touch 0.1/espera 20.3. Teste humano aprovado (dono: "Aprovar T1.13 e fechar CA-1-032/033/037"); revalidação do zero na v0.0.62.
- T1.14 e demais tasks mantêm suas dependências.

## Próxima ação

Champion solicita a próxima task quando quiser (T1.14 é a elegível por dependência — exportação sanitizada, autorização e auditoria; fecha a SPEC-1-006).

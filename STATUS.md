# Status

**Fase atual:** Fase 3 — Transcrições de reuniões (100% nativo Skip)
**Estado:** T3.1 (ingestão) e T3.2 (análise IA) implementadas e com bugs de UI corrigidos — aguardando teste humano
**Atualizado em:** 2026-10-27

## Fase 2 — ENCERRADA (26/10/2026)

5/5 tasks · 20 CAs + aceite · roteiro 29/29 · v0.0.80. Dossiê: artifacts/t25-dossie-aceite-fase2.md.

## Fase 3 — em andamento

- **T3.1 ✓ (v0.0.95):** ingestão — tipo "transcricao" (texto ≥ 50 chars), aba Transcrições no cartão, auditoria transcricao_criada. Migração 0023.
- **T3.2 ✓ (v0.0.88):** análise IA — hook POST /workspace/{id}/analisar chama $ai.chat (alias fast); resultado em coleção NOVA transcricao_analises (0024) mesclado na listagem; re-análise; auditado transcricao_analisada. UI: Analisar/Re-analisar + painel com resumo, decisões, compromissos, riscos, próximos passos.
- **Prova com transcrição real (27/10):** reunião de alinhamento RVV Comercial no STARIAN-001 → resumo coerente + 3 decisões com autor + 3 compromissos com responsável e prazo + 3 riscos + próximos passos.
- **T3.3 (pendente):** agente analista conversacional ($ai.agent com tools do projeto).
- **T3.4 (pendente):** roteiro integrado + dossiê + aceite da Fase 3.

## Lições técnicas acumuladas (Fase 3)

1. **Tipo novo exige atualizar TODOS os pontos:** hook de criação + validação + dropdown de Tipo + campo de conteúdo condicional + label do botão. Faltou o dropdown e o campo → a feature existia mas era impossível de usar pela UI.
2. **Seção nova no fim de cartão longo é invisível:** o Workspace era a última seção; resolver com atalhos que FOCAM a seção (o dialog do Radix não rola por script — position fixed, sem container rolável).
3. **Migration que ADICIONA CAMPO em coleção existente não persiste** (2ª ocorrência) — usar coleção nova.
4. **Hook novo em arquivo novo pode dar 404** na primeira versão; **patch em hook existente não recarrega** — reescrever o arquivo inteiro.

## Dívidas rastreadas

- Fixture u-revisor 401 (F2) · projetos sem sp_folder orientam pedir mapeamento (F2) · picker no modo edição (UX) · arquivos de prova em _TESTE_FASE2 · campos an_* da 0023 não existem no schema vivo (inofensivo — limpar na faxina da fase).

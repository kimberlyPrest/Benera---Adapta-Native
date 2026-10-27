# Status

**Fase atual:** Fase 3 — Transcrições de reuniões (100% nativo Skip, decisão do dono 27/10)
**Estado:** T3.1 (ingestão) e T3.2 (análise IA) implementadas — aguardando teste humano; T3.3 e T3.4 pendentes
**Atualizado em:** 2026-10-27

## Fase 2 — ENCERRADA (26/10/2026)

5/5 tasks · 20 CAs + aceite · roteiro 29/29 · v0.0.80. Dossiê: artifacts/t25-dossie-aceite-fase2.md.

## Fase 3 — em andamento

- **Decisão do dono (27/10):** transcrições de reuniões, motor 100% nativo Skip ($ai.chat no hook + agente nativo para conversa — sem chave externa; aliases fast/reasoning verificados no guia da plataforma).
- **T3.1 implementada (v0.0.82):** ingestão — tipo "transcricao" no workspace (texto ≥ 50 chars obrigatório), aba Transcrições no cartão, auditoria transcricao_criada. Migração 0023.
- **T3.2 implementada (v0.0.88):** análise IA server-side — hook POST /workspace/{id}/analisar chama $ai.chat (alias fast) com prompt de analista sênior (resumo, decisões, compromissos com responsável/prazo, riscos, próximos passos em JSON); resultado persistido na coleção NOVA transcricao_analises (0024) e mesclado na listagem; re-análise permitida; auditado transcricao_analisada. UI: botão Analisar/Re-analisar + painel da análise no item.
- **T3.3 (pendente):** agente analista conversacional ($ai.agent com tools do projeto) — consultor pergunta e cruza dados.
- **T3.4 (pendente):** roteiro integrado + dossiê + aceite da Fase 3.

## Lições técnicas (Fase 3)

- CONFIRMADO de novo: migration que ADICIONA CAMPO em coleção existente não persiste na instância viva (0023 an_* em workspace_items — set() silenciosamente descartado). Coleção NOVA persiste (0024 transcricao_analises). Workaround definitivo: análise em coleção própria 1:1 por item.
- Hook novo em arquivo novo: 404 na primeira versão (v0.0.78 padrão) — reescrita força re-registro.
- Patch em hook existente não recarrega — reescrever o arquivo inteiro.

## Dívidas rastreadas

- Fixture u-revisor 401 (F2) · projetos sem sp_folder orientam pedir mapeamento (F2) · picker no modo edição (UX) · arquivos de prova em _TESTE_FASE2 a limpar · campos an_* da 0023 não existem no schema vivo (inofensivo — análise vive na 0024; limpar a 0023 na faxina da fase).

# Status

**Fase atual:** Fase 3 — Transcrições de reuniões
**Estado:** T3.4 executada (roteiro 24/24 + dossiê) — aguardando aceite humano para encerrar a fase
**Atualizado em:** 2026-10-27

## Fases encerradas

- **Fase 1** (26/10): central operacional, 16/16 tasks, 42/42 CAs. Dossiê: artifacts/t116-dossie-aceite-fase1.md
- **Fase 2** (26/10): integração SharePoint completa, 5/5 tasks, 20 CAs, roteiro 29/29. Dossiê: artifacts/t25-dossie-aceite-fase2.md

## Fase 3 — em andamento

- **T3.1 ✓** ingestão de transcrições (tipo transcricao, aba no cartão, 0023)
- **T3.2 ✓** análise IA nativa ($ai.chat alias fast; coleção nova transcricao_analises 0024; join na listagem; auditada). Formato v1 aprovado: resumo, decisões com autor, compromissos com responsável/prazo, riscos, próximos passos.
- **T3.3 ADIADA** (decisão do champion 27/10) — agente conversacional fica para a próxima frente
- **T3.4 ✓** roteiro 24/24 + dossiê: artifacts/t34-dossie-aceite-fase3.md
- **Pendente:** aceite humano da Fase 3

## Dívidas rastreadas

1. Calibração do motor de análise — gatilho: 5 transcrições reais na base, revisar com o champion
2. T3.3 agente conversacional (próxima frente)
3. Corte de 12k caracteres por análise — chunking para reuniões longas
4. Campos an_* da 0023 não existem no schema vivo (inofensivo; limpar na faxina)
5. Fixture u-revisor 401 · projetos sem sp_folder · picker no modo edição · itens de teste a limpar

## Lições técnicas (Fase 3)

- Tipo novo exige atualizar TODOS os pontos: hook, validação, dropdown, campo condicional, label do botão
- Seção nova no fim de cartão longo é invisível → atalhos que FOCAM (dialog Radix não rola por script)
- Em item com texto longo + resultado derivado, o RESULTADO vem primeiro
- Migration que adiciona campo em coleção existente não persiste → coleção nova
- Hook novo pode dar 404 na primeira versão; patch em hook existente não recarrega → reescrever o arquivo

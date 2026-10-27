# Status

**Fase atual:** nenhuma aberta — Fases 1, 2 e 3 ENCERRADAS
**Estado:** aguardando decisão do escopo da próxima frente
**Atualizado em:** 2026-10-27 20:17

## Fases encerradas

### Fase 1 — Central operacional (encerrada 26/10)
16/16 tasks · 42/42 CAs · 7/7 SPECs · roteiro 32/32. Dossiê: `artifacts/t116-dossie-aceite-fase1.md`.
Cliente/projeto → cartão 360 → esteira configurável → Kanban → tarefas/checklists → bloqueios/handoffs → workspace → painel → touch time/ciclo/baseline → exportação sanitizada.

### Fase 2 — Integração SharePoint (encerrada 26/10)
5/5 tasks · 20 CAs · roteiro 29/29. Dossiê: `artifacts/t25-dossie-aceite-fase2.md`.
Escrita (device flow) · navegador server-side · escopo por projeto (admin 100%, consultor só pastas alocadas) · vínculo workspace↔SharePoint (fecha badge ORIGEM PENDENTE) · upload auditado (destino fixo = sp_folder).

### Fase 3 — Transcrições de reuniões (encerrada 27/10)
T3.1 + T3.2 + T3.4 · roteiro 24/24. Dossiê: `artifacts/t34-dossie-aceite-fase3.md` · v0.0.96.
Ingestão (tipo transcricao, aba no cartão) · análise IA nativa ($ai.chat alias fast → resumo, decisões com autor, compromissos com responsável/prazo, riscos, próximos passos; coleção nova transcricao_analises) · tudo auditado. **T3.3 (agente conversacional) adiada por decisão do champion.**

## Dívidas rastreadas

1. **Calibração do motor de análise** — gatilho: 5 transcrições reais na base; revisar prompt e vocabulário técnico com o champion. Formato v1 aprovado.
2. **T3.3 — agente analista conversacional** ($ai.agent com tools do projeto).
3. Corte de ~12k caracteres por análise — chunking para reuniões longas.
4. Campos an_* da migração 0023 não existem no schema vivo (inofensivo; análise vive na 0024) — limpar na faxina.
5. Fixture u-revisor 401 · projetos sem sp_folder · picker do SharePoint no modo edição · itens de teste em _TESTE_FASE2.

## Lições técnicas acumuladas

- Tipo novo exige atualizar TODOS os pontos: hook, validação, dropdown, campo condicional, label do botão.
- Seção nova no fim de cartão longo é invisível → atalhos que FOCAM a seção (dialog Radix não rola por script).
- Em item com texto longo + resultado derivado, o RESULTADO vem primeiro.
- Migration que adiciona campo em coleção existente não persiste → usar coleção nova.
- Hook novo pode dar 404 na primeira versão; patch em hook existente não recarrega → reescrever o arquivo inteiro.
- Upload session do Graph exige Content-Range mesmo para arquivo único.

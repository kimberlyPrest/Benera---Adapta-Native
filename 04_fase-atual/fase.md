# Fase 1 — Central operacional manual e baseline

## Objetivo

Entregar a primeira superfície de trabalho da Benera: um workspace em que um projeto real ou controlado é cadastrado, percorre etapas configuráveis, recebe tarefas e responsáveis, registra bloqueios/handoffs, concentra evidências e aparece em um painel operacional.

## Inclui

- autenticação por convite, papéis mínimos e autorização server-side;
- cadastro de cliente, tipo de serviço e projeto;
- cartão do projeto, Kanban, lista, filtros, prioridade, prazo e próxima ação;
- etapas configuráveis com versão e reversão;
- tarefas/checklists, filas individuais, bloqueios e handoffs idempotentes;
- notas internas, comentários, documentos/links e registro de entrega;
- linha do tempo, auditoria, exportação sanitizada;
- registro separado de touch time, espera, ciclo e baseline;
- demonstração integrada com fixture sintética e projeto-piloto controlado.

## Fora desta fase

Portal do cliente, upload externo, integração direta com SharePoint, ingestão automática de transcrições, IA de proposta/diagnóstico, timesheet avançado, organogramas e remuneração.

## Preparação

- confirmar o repositório/ambiente de implementação;
- criar usuários de teste e fixture sintética sem PII;
- escolher projeto-piloto e tipo de serviço;
- homologar etapas iniciais: Entrada, Kick-off, Diagnóstico, Entrega e Encerrado;
- definir política mínima de acesso, retenção e exportação;
- definir quem valida o fluxo operacional.

## Demonstração visível

Um administrador convida usuários; cadastra cliente e projeto; configura o fluxo; atribui uma tarefa; o consultor registra evidência e bloqueio; o gestor realiza handoff; o painel mostra etapa, atraso, responsável, bloqueio e tempos; a auditoria reconstitui a sequência.

## Critérios de aceite da fase

- **CA-F1-06:** painel separa touch time, espera e ciclo; exportação é sanitizada e auditada. **Detalhamento:** CA-1-031..CA-1-037 — TODOS fechados.
- **CA-F1-07:** fluxo integrado é demonstrado e o aceite humano registra evidência por critério. **Detalhamento:** CA-1-038..CA-1-042 — TODOS fechados (roteiro 32/32; aceite humano registrado).

## SPECs desta onda

| SPEC | Resultado |
|---|---|
| SPEC-1-006 | painel, baseline, auditoria e exportação — COMPLETA (CA-1-031..037) |
| SPEC-1-007 | piloto integrado e aceite — COMPLETA (CA-1-038..042) |

## Tasks

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência esperada | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|
| T1.1–T1.12 | Concluídas (CA-1-001..031) — ver changelog e STATUS.md para o histórico completo por task | Ethos | SPEC-1-001..006 | CA-1-001..031 com teste humano aprovado | RED/GREEN/REGRESSÃO por task | dossiê por task no changelog | — | concluídas 2026-10-05 a 2026-10-23 (v0.0.2→58) |
| T1.13 | Implementar registro separado de touch time, espera, ciclo e baseline | Ethos | SPEC-1-006 | CA-1-032/CA-1-033/CA-1-037: tempos separados, baseline com período/amostra e sem promessa de ganho | GREEN + REFACTOR/REGRESSÃO da SPEC-1-006 | relatório de baseline com relógio, período, amostra e limitações | T1.6 e T1.12 concluídas | concluída 2026-10-26 — CA-1-032/033/037 com teste humano aprovado (dono: "Aprovar T1.13 e fechar CA-1-032/033/037"); revalidação do zero na v0.0.62 |
| T1.14 | Implementar exportação sanitizada, autorização de exportar e auditoria de eventos | Ethos | SPEC-1-006 | CA-1-034..CA-1-036: export seguro, auditado e sem fórmula executável | RED/GREEN/REGRESSÃO — exportação negativa, célula sintética =1+1 e auditoria | arquivo sanitizado, hash, log de exportação e prova negativa | T1.2, T1.12 e T1.13 concluídas | concluída 2026-10-26 (v0.0.63) — teste humano aprovado ("vamos em frente"); sanitização "=1+1"→'=1+1 provada no CSV e no JSON; config_changed 500→300→500 reversível; painel_consulta a cada consulta; determinismo provado |
| T1.15 | Configurar fixture e projeto-piloto controlado com etapas, tarefas, documento e responsável | Ethos | SPEC-1-007 | CA-1-039/CA-1-040: cada CA tem evidência/estado e a fixture não contém PII | GREEN da SPEC-1-007 — preparação do piloto | snapshot sanitizado da fixture e configuração aplicada | T1.4, T1.6, T1.9, T1.10, T1.12 e T1.14 concluídas | concluída 2026-10-26 — PILOTO-F1-001 configurado (3 tarefas c/ evidência esperada, 1 checklist, doc pendente + nota, owner consultor); snapshot com varredura PII de 5 padrões: 0 achados, LIMPO (artifacts/t115-snapshot-fixture.json) |
| T1.16 | Executar roteiro integrado e montar dossiê de aceite CA a CA da Fase 1 | Ethos | SPEC-1-007 | CA-1-038..CA-1-042: fluxo completo, evidências, limitações e aceite humano | GREEN + REFACTOR/REGRESSÃO da SPEC-1-007 | dossiê CA a CA, evidências, pendências e veredito humano | T1.13, T1.14 e T1.15 concluídas | concluída 2026-10-26 — roteiro integrado 32/32 passos OK (login→exportação, RED paths incluídos); dossiê CA-1-001..041 com evidência (artifacts/t116-dossie-aceite-fase1.md); **CA-1-042 APROVADO** — aceite humano registrado 2026-10-26 17:09 (dono: "Aprovar a Fase 1 (CA-1-042)") |

## Estado da fase

**Fase 1 ENCERRADA (2026-10-26).** 16/16 tasks concluídas (2026-10-05 a 2026-10-26, Skip 63138 v0.0.2→63, QA ok); 42/42 critérios de aceite fechados com evidência individual; 7/7 SPECs completas; aceite humano registrado pelo dono. Dívidas declaradas rastreadas para a próxima fase: templates de e-mail com host do preview (reverter na publicação em produção); edição concorrente de workspace = última escrita vence (documentado); duplicado KLABIN inativável pela tela. Fixture de demonstração: PILOTO-F1-001 ativo; PROJ-F1-001 e ROTEIRO-F1-001 preservados como histórico (baseline e prova do roteiro).

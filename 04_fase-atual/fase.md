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

- **CA-F1-06:** painel separa touch time, espera e ciclo; exportação é sanitizada e auditada. **Detalhamento:** CA-1-031..CA-1-037.
- **CA-F1-07:** fluxo integrado é demonstrado e o aceite humano registra evidência por critério. **Detalhamento:** CA-1-038..CA-1-042.

## SPECs abertas nesta onda

| SPEC | Resultado |
|---|---|
| SPEC-1-006 | painel, baseline, auditoria e exportação |
| SPEC-1-007 | piloto integrado e aceite |

## Tasks

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência esperada | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|
| T1.1–T1.12 | Concluídas (CA-1-001..031) — ver changelog e STATUS.md para o histórico completo por task | Ethos | SPEC-1-001..006 | CA-1-001..031 com teste humano aprovado | RED/GREEN/REGRESSÃO por task | dossiê por task no changelog | — | concluídas 2026-10-05 a 2026-10-23 (v0.0.2→58) |
| T1.13 | Implementar registro separado de touch time, espera, ciclo e baseline | Ethos | SPEC-1-006 | CA-1-032/CA-1-033/CA-1-037: tempos separados, baseline com período/amostra e sem promessa de ganho | GREEN + REFACTOR/REGRESSÃO da SPEC-1-006 | relatório de baseline com relógio, período, amostra e limitações | T1.6 e T1.12 concluídas | concluída 2026-10-26 — CA-1-032/033/037 com teste humano aprovado (dono: "Aprovar T1.13 e fechar CA-1-032/033/037"); revalidação do zero na v0.0.62 (RED 403/400; touch/espera distintas com espera = ciclo − touch piso 0; incompleto ≠ zero; baseline 20.6d BRT amostra 3·2·273 com corte declarado e nota anti-ganho; determinismo; append-only PATCH 400, inativação preserva evento, 8 eventos na auditoria; limpeza touch 0; regressão geral). Bug do ciclo (parse ZZ) corrigido em v0.0.62; e2e pela UI (apontar 45 min → touch 2h→2.8h → painel ciclo 20.4/touch 0.1/espera 20.3) |
| T1.14 | Implementar exportação sanitizada, autorização de exportar e auditoria de eventos | Ethos | SPEC-1-006 | CA-1-034..CA-1-036: export seguro, auditado e sem fórmula executável | RED/GREEN/REGRESSÃO — exportação negativa, célula sintética =1+1 e auditoria | arquivo sanitizado, hash, log de exportação e prova negativa | T1.2, T1.12 e T1.13 concluídas | a fazer |
| T1.15 | Configurar fixture e projeto-piloto controlado com etapas, tarefas, documento e responsável | Ethos | SPEC-1-007 | CA-1-039/CA-1-040: cada CA tem evidência/estado e a fixture não contém PII | GREEN da SPEC-1-007 — preparação do piloto | snapshot sanitizado da fixture e configuração aplicada | T1.4, T1.6, T1.9, T1.10, T1.12 e T1.14 concluídas | a fazer |
| T1.16 | Executar roteiro integrado e montar dossiê de aceite CA a CA da Fase 1 | Ethos | SPEC-1-007 | CA-1-038..CA-1-042: fluxo completo, evidências, limitações e aceite humano | GREEN + REFACTOR/REGRESSÃO da SPEC-1-007 | dossiê CA a CA, evidências, pendências e veredito humano | T1.13, T1.14 e T1.15 concluídas | a fazer |

## Estado da fase

T1.1–T1.13 concluídas (2026-10-05 a 2026-10-26, Skip 63138 v0.0.62, QA ok; testes humanos aprovados pelo champion; CA-1-001..033 + 037 com evidência — SPECs 1-001..1-005 COMPLETAS, SPEC-1-006 em andamento: restam CA-1-034..036 na T1.14). Pendência da T1.2 (UI de membros) resolvida na T1.3. Demais tasks a fazer; nenhuma fase avançou.

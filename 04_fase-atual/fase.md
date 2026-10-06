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

- **CA-F1-01:** usuários convidados acessam somente workspace/projetos autorizados e os papéis são aplicados no servidor. **Detalhamento:** CA-1-001..CA-1-006.
- **CA-F1-02:** projeto-piloto é criado com cartão completo, aparece no Kanban e pode ser filtrado por etapa, responsável e atraso. **Detalhamento:** CA-1-007..CA-1-011.
- **CA-F1-03:** administrador altera e reverte uma etapa/configuração sem reescrever o histórico existente. **Detalhamento:** CA-1-012..CA-1-018.
- **CA-F1-04:** tarefa/checklist, bloqueio e handoff funcionam com responsável, prazo, motivo e histórico. **Detalhamento:** CA-1-019..CA-1-025.
- **CA-F1-05:** documentos, notas, comentários e entrega ficam vinculados ao projeto com acesso controlado. **Detalhamento:** CA-1-026..CA-1-030.
- **CA-F1-06:** painel separa touch time, espera e ciclo; exportação é sanitizada e auditada. **Detalhamento:** CA-1-031..CA-1-037.
- **CA-F1-07:** fluxo integrado é demonstrado e o aceite humano registra evidência por critério. **Detalhamento:** CA-1-038..CA-1-042.


## SPECs abertas nesta onda

| SPEC | Resultado |
|---|---|
| SPEC-1-001 | acesso, papéis e isolamento |
| SPEC-1-002 | cliente, projeto e cartão 360 |
| SPEC-1-003 | esteira configurável e Kanban |
| SPEC-1-004 | tarefas, bloqueios e handoffs |
| SPEC-1-005 | workspace interno |
| SPEC-1-006 | painel, baseline, auditoria e exportação |
| SPEC-1-007 | piloto integrado e aceite |

## Tasks

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência esperada | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|
| T1.1 | Implementar convite, login e perfis mínimos da Fase 1 com usuários sintéticos | Ethos | SPEC-1-001 | CA-1-001/CA-1-002: convite, ativação e matriz de papéis funcionam | GREEN da SPEC-1-001 — convite/login e matriz de papéis | capturas de login por papel + matriz de permissões | repositório/ambiente de homologação disponível; fixture F1 criada | concluída 2026-10-05 — CA-1-001 com teste humano aprovado; CA-1-002 validado com o teste da matriz ao vivo (9 passos) |
| T1.2 | Aplicar autorização server-side por workspace/projeto, revogação e auditoria de acesso | Ethos | SPEC-1-001 | CA-1-003/CA-1-004/CA-1-005/CA-1-006: acesso cruzado negado, revogação efetiva, eventos auditados e nenhum segredo exposto | RED/GREEN/REGRESSÃO — tentativas diretas, revogação e inspeção de logs | logs sanitizados e prova negativa de usuário sem vínculo/segredo | T1.1 concluída | concluída 2026-10-05 — provas RED/GREEN/REGRESSÃO/AUDITORIA aprovadas e validadas ao vivo pelo champion; UI de gestão de membros registrada como pendência para T1.3 |
| T1.3 | Criar modelo e CRUD mínimo de cliente, tipo de serviço e projeto | Ethos | SPEC-1-002 | CA-1-007: cliente/projeto são criados com campos mínimos | GREEN da SPEC-1-002 — criação com ACME-FIXTURE/PROJ-F1-001 | registros persistidos e captura do formulário/cartão inicial | ambiente disponível; fixture F1 criada | a fazer |
| T1.4 | Implementar cartão 360, listagem, filtros e inativação preservando histórico | Ethos | SPEC-1-002 | CA-1-008..CA-1-011: cartão completo, filtros, auditoria e inativação | GREEN + REFACTOR/REGRESSÃO da SPEC-1-002 | capturas do cartão/filtros + timeline de alteração/inativação | T1.2 e T1.3 concluídas | a fazer |
| T1.5 | Implementar configuração de etapas com ordem, critérios, versão e rollback | Ethos | SPEC-1-003 | CA-1-012/CA-1-013/CA-1-018: administrador configura, versiona e reverte | GREEN + REFACTOR/REGRESSÃO — versão 1/2 e rollback | diff de configuração, histórico de versões e captura do rollback | T1.1 concluída; etapas iniciais homologadas | a fazer |
| T1.6 | Implementar Kanban/lista, filtros e transições válidas com histórico | Ethos | SPEC-1-003 | CA-1-014..CA-1-017: quadro/filtros/transição válida, inválida e permissão | GREEN + caminho de erro da SPEC-1-003 | capturas do quadro/lista + eventos de transição/negação | T1.4 e T1.5 concluídas | a fazer |
| T1.7 | Criar tarefas e checklists com responsável, prazo, status e evidência esperada | Ethos | SPEC-1-004 | CA-1-019/CA-1-020: tarefa e checklist obrigatório funcionam | GREEN da SPEC-1-004 — tarefas da fixture | capturas de tarefa/checklist e estado pendente/concluído | T1.4 concluída | a fazer |
| T1.8 | Implementar bloqueio, retorno para correção e handoff idempotente | Ethos | SPEC-1-004 | CA-1-021..CA-1-023: bloqueio/retorno/handoff com motivo e sem duplicata | RED/GREEN/REGRESSÃO — bloqueio incompleto, retorno e retry | prova negativa + registro de handoff único + timeline | T1.5 e T1.7 concluídas | a fazer |
| T1.9 | Implementar fila individual, vencidos e bloqueados por responsável | Ethos | SPEC-1-004 | CA-1-024/CA-1-025: fila mostra próprias, vencidas, bloqueadas e concluídas | GREEN da SPEC-1-004 — fila de u-consultor | captura da fila filtrada e contagem de estados | T1.7 e T1.8 concluídas | a fazer |
| T1.10 | Implementar notas internas, comentários, documentos/links e registro de entrega | Ethos | SPEC-1-005 | CA-1-026/CA-1-027/CA-1-028: itens e entrega ficam vinculados ao projeto | GREEN da SPEC-1-005 — workspace de PROJ-F1-001 | capturas do workspace e itens persistidos | T1.2 e T1.4 concluídas | a fazer |
| T1.11 | Aplicar permissões herdadas, timeline e fallback manual para destino externo | Ethos | SPEC-1-005 | CA-1-029/CA-1-030: acesso restrito, timeline e fallback sem perda | RED/GREEN/REGRESSÃO — usuário sem vínculo e storage indisponível | prova negativa + timeline + registro de fallback | T1.10 concluída | a fazer |
| T1.12 | Implementar painel operacional por etapa, responsável, atraso, bloqueio e prioridade | Ethos | SPEC-1-006 | CA-1-031: painel mostra agregados operacionais filtráveis | GREEN da SPEC-1-006 — eventos sintéticos | capturas do painel com filtros e totais | T1.6, T1.8 e T1.9 concluídas | a fazer |
| T1.13 | Implementar registro separado de touch time, espera, ciclo e baseline | Ethos | SPEC-1-006 | CA-1-032/CA-1-033/CA-1-037: tempos separados, baseline com período/amostra e sem promessa de ganho | GREEN + REFACTOR/REGRESSÃO da SPEC-1-006 | relatório de baseline com relógio, período, amostra e limitações | T1.6 e T1.12 concluídas | a fazer |
| T1.14 | Implementar exportação sanitizada, autorização de exportar e auditoria de eventos | Ethos | SPEC-1-006 | CA-1-034..CA-1-036: export seguro, auditado e sem fórmula executável | RED/GREEN/REGRESSÃO — exportação negativa, célula sintética =1+1 e auditoria | arquivo sanitizado, hash, log de exportação e prova negativa | T1.2, T1.12 e T1.13 concluídas | a fazer |
| T1.15 | Configurar fixture e projeto-piloto controlado com etapas, tarefas, documento e responsável | Ethos | SPEC-1-007 | CA-1-039/CA-1-040: cada CA tem evidência/estado e a fixture não contém PII | GREEN da SPEC-1-007 — preparação do piloto | snapshot sanitizado da fixture e configuração aplicada | T1.4, T1.6, T1.9, T1.10, T1.12 e T1.14 concluídas | a fazer |
| T1.16 | Executar roteiro integrado e montar dossiê de aceite CA a CA da Fase 1 | Ethos | SPEC-1-007 | CA-1-038..CA-1-042: fluxo completo, evidências, limitações e aceite humano | GREEN + REFACTOR/REGRESSÃO da SPEC-1-007 | dossiê CA a CA, evidências, pendências e veredito humano | T1.13, T1.14 e T1.15 concluídas | a fazer |

## Estado da fase

T1.1 e T1.2 concluídas em 2026-10-05 (Skip 63138 v0.0.7, QA ok; testes humanos aprovados pelo champion; CA-1-001..006 com evidência). Pendência registrada: UI de gestão de membros (conceder/revogar) entra na T1.3. Demais tasks a fazer; nenhuma fase avançou.
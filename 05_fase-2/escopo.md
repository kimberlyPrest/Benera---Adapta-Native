# Fase 2 — Integração SharePoint (origem e publicação de documentos)

## Objetivo

Completar o desenho do workspace da Fase 1: documento/entrega passa a puxar a origem do SharePoint BENERACORP (biblioteca "BENERA CORP - Documentos", pasta CONSULTORIA) e publicar arquivos no SharePoint — eliminando o registro manual (badge ORIGEM PENDENTE) e o atrito de subir documento à mão.

## Decisão do dono (2026-10-26)

- Frente principal: **Integração SharePoint** (recomendada e aprovada)
- Formato: **Fase completa** (5 tasks, SPECs formais, dossiê de aceite)
- Ambiente: **mesmo projeto Skip 63138** (base v0.0.63 homologada)
- Referência do dono: biblioteca já acessível em leitura pelo Maestro; caminho local espelhado `C:\Users\FABIOFORCASSIN\BENERA\Fabio Forcassin\BENERA CORP - Documentos\CONSULTORIA`

## Inclui

- re-consentimento de escrita (Sites.ReadWrite.All) via device flow com o app oficial da MS — participação do dono;
- navegador de arquivos do SharePoint na UI (server-side, token nunca no front);
- vínculo documento workspace ↔ arquivo SharePoint (badge ORIGEM PENDENTE fecha sozinho);
- upload de arquivo do workspace para o SharePoint (pasta do projeto ou pasta de teste);
- roteiro integrado da fase + dossiê de aceite CA a CA.

## Fora desta fase

Portal do cliente, ingestão automática de transcrições, IA de proposta/diagnóstico, alteração da estrutura 01–90 do Starium (só leitura/vínculo; upload só em pasta de teste ou pasta indicada pelo dono), timesheet, organogramas e remuneração.

## Estado técnico de partida (fatos)

- Leitura: OneDrive pessoal OK + Sites.Read.All OK (biblioteca BENERACORP acessível).
- Escrita: Sites.ReadWrite.All NÃO concedido — upload no BENERA CORP responde 403 (registrado 13/10). Primeiro critério da fase é destravar isso.
- Credencial: token em `scripts/.benera_token.json` (fora do repo), renovado automaticamente; app oficial "Microsoft Graph Command Line Tools" (device flow — caminho preferido pelo dono, sem portal Entra).

## Riscos e plano B

- Consentimento depende do dono (device flow) → T2.1 começa com o passo a passo pronto para ele executar.
- Permissão pode exigir aprovação de admin do tenant → se o consent falhar, registrar impedimento e escalar ao dono (ele é o admin).
- Não tocar nas pastas do Starium sem autorização → upload de prova em pasta dedicada `_TESTE_FASE2`.

## Critérios de aceite da fase

- **CA-F2-01:** escrita no SharePoint provada (upload/download íntegro, auditado). CA-2-001..004.
- **CA-F2-02:** navegador seguro (server-side, escopo herdado, token nunca exposto). CA-2-005..008.
- **CA-F2-03:** vínculo workspace↔SharePoint fecha o ORIGEM PENDENTE e é auditado. CA-2-009..012.
- **CA-F2-04:** upload do workspace para o SharePoint auditado, com nomenclatura e falha visível. CA-2-013..016.
- **CA-F2-05:** roteiro integrado + dossiê CA a CA + aceite humano. CA-2-017..019.

## SPECs

| SPEC | Resultado |
|---|---|
| SPEC-2-001 | conexão de escrita no SharePoint (re-consentimento + provas de upload/download) |
| SPEC-2-002 | navegador de arquivos do SharePoint (server-side, escopo herdado) |
| SPEC-2-003 | vínculo documento workspace ↔ arquivo SharePoint |
| SPEC-2-004 | upload de arquivo do workspace para o SharePoint |
| SPEC-2-005 | roteiro integrado e aceite da Fase 2 |

## Tasks

| ID | Task | Dono | SPEC | Critério | Pré-condições | Status |
|---|---|---|---|---|---|---|
| T2.1 | Re-consentimento de escrita + provas de upload/download na biblioteca (pasta _TESTE_FASE2) | Ethos + dono (device flow) | SPEC-2-001 | CA-2-001..004 | Fase 1 encerrada | aguardando autorização |
| T2.2 | Navegador de arquivos do SharePoint na UI (server-side) | Ethos | SPEC-2-002 | CA-2-005..008 | T2.1 | a fazer |
| T2.3 | Vínculo documento workspace ↔ arquivo SharePoint (badge fecha sozinho) | Ethos | SPEC-2-003 | CA-2-009..012 | T2.1 e T2.2 | a fazer |
| T2.4 | Upload de arquivo do workspace para o SharePoint (auditado) | Ethos | SPEC-2-004 | CA-2-013..016 | T2.1 e T2.3 | a fazer |
| T2.5 | Roteiro integrado da Fase 2 + dossiê de aceite CA a CA | Ethos | SPEC-2-005 | CA-2-017..019 | T2.1–T2.4 | a fazer |

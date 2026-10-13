# DEBUG T1.7 — Dropdown de responsável vazio e botão "Criar tarefa" morto no perfil do consultor

**Data:** 2026-10-13 · **Task:** T1.7 · **Reportado por:** champion (teste humano)

## Debug Summary

**Task e problema:** consultor não conseguia incluir o responsável (dropdown vazio) nem criar a tarefa no seu perfil; no perfil do admin funcionou.

**Reprodução:** login u-consultor → abrir cartão de projeto com vínculo → Nova tarefa → dropdown "Responsável" vazio; clicar Criar tarefa → erro 400.

**Causa raiz (cadeia demonstrada):**
1. Dropdown vazio: hook `usuarios-listar` (da T1.3) só permite admin/líder — consultor recebe 403 e o campo fica sem opções (prova: 403 "Somente administrador ou líder podem listar usuários.").
2. Botão morto: o front envia assignee_id vazio (dropdown vazio) → 400 por campo obrigatório — a trava server-side funcionando corretamente; a falha era o dropdown upstream.

**Correção (mínima, na task):**
- Hook `usuarios-listar`: consultor/revisor recebem lista PARCIAL (id + nome), sem email e sem papel (linha vermelha LGPD/segurança); admin/líder continuam com lista completa. Sem auth 401.
- Front: dropdown de responsável filtra revisores (não executam) e marca "(consultor)".

**Verificação automática (v0.0.38, QA verde):**
- consultor lista usuários: 5 nomes, email exposto: False
- consultor cria tarefa com vínculo: 201 (com e sem checklist)
- consultor sem vínculo (PROJ-REG-001): 403 auditado
- revisor: lista parcial (não vazia), sem email
- regressão: esteira, kanban, /projetos OK

**Gate atual:** fechado com teste humano aprovado (reteste).

**Resíduo:** tarefas de prova do debug ("Prova do debug T1.7", "Tarefa criada pelo consultor", "Tarefa consultor com checklist") + 3 lixos pré-fix ficaram em PROJ-F1-001; remoção exige superusuário (regras nulas) — faxina pendente de decisão.

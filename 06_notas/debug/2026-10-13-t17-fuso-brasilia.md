# DEBUG T1.7 — Prazo de "hoje" recusado às 21h (fuso)

**Data:** 2026-10-13 · **Task:** T1.7 · **Detectado em:** revalidação do zero (concluir-task)

## Debug Summary

**Task e problema:** criação de tarefa com due_date do próprio dia recusada com "Prazo no passado não é permitido." às ~21h de Brasília.

**Reprodução:** POST com due_date = data local às 21h BRT → 400.

**Causa raiz:** hook comparava due_date contra `new Date().toISOString().slice(0,10)` — data UTC. Às 21h BRT o UTC já está no dia seguinte, então "hoje" (BRT) < "hoje" (UTC) e a recusa dispara.

**Correção:** "hoje" = `new Date(Date.now() - 3h).toISOString().slice(0,10)` (Brasília, UTC-3) em tarefas-criar e no sinal de atraso em tarefas-listar (mesmo padrão de comparação lexicográfica).

**Verificação automática (v0.0.39):** criação com due_date de hoje → 201; prazo 2025-01-01 → 400; regressão OK.

**Gate atual:** fechado com teste humano aprovado (reteste).

**Regra:** qualquer comparação "hoje vs prazo" no produto usa BRT (UTC-3), nunca UTC puro.

# AP-2026-10-13-t17-fuso-comparacoes — "hoje" é Brasília, não UTC

**Origem:** revalidação T1.7 (Skip 63138) · **Data:** 2026-10-13

**Sinal:** prazo do próprio dia recusado às 21h BRT ("Prazo no passado").

**Aprendizado:** toISOString() é UTC — às 21h BRT o UTC já está no dia seguinte. Toda comparação "hoje vs prazo" (validação de criação, sinal de atraso, vencidos) deve usar BRT: new Date(Date.now() - 3h).toISOString().slice(0,10).

**Regra aplicada (v0.0.39, tarefas-criar + tarefas-listar).**

**Reutilizável:** qualquer data-limite no produto (vencidos de T1.9, prazos de projeto, lembretes).

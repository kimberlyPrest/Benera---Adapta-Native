# AP-2026-10-22-t110-descobribilidade — Seção nova abaixo de lista longa parece inexistente

**Origem:** T1.10 (Skip 63138) · **Data:** 2026-10-22

**Sinal:** dono não achou as notas no Workspace — a seção renderizava, mas ficava no fim do cartão após 27 tarefas de teste; e o navegador estava com bundle antigo cacheado.

**Aprendizado:** seção nova adicionada ABAIXO de uma lista que cresce sem limite (tarefas, itens) é invisível na prática — quem testa para no conteúdo longo. Sempre que uma task adiciona seção ao cartão: (1) posicionar acima da lista longa ou com âncora/atalho; (2) limpar dados de teste antes do teste humano; (3) lembrar hard refresh (bundle hash muda por build).

**Regra aplicada (v0.0.52/53: espaçamento; faxina recomendada).**

**Reutilizável:** qualquer UI com seções empilhadas e listas vivas.

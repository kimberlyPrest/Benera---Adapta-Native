# AP-2026-10-13-encerrado-no-quadro — Card movido para a última coluna não pode sumir

**Origem:** teste do champion (T1.6) · **Data:** 2026-10-13

**Sinal:** ao encerrar o EMBALAGEM, o card sumia do Kanban — a listagem filtrava active=true e a inativação marca o projeto como inativo.

**Aprendizado:** o quadro deve mostrar o card na coluna final (Encerrado), não removê-lo — a remoção visual contradiz o modelo mental do usuário e esconde o resultado da ação. Listagem do Kanban aceita parâmetro encerrados=1; lista de gestão mantém filtro.

**Regra aplicada (v0.0.34).**

**Reutilizável:** qualquer quadro/fluxo com estado final (o fim não é desaparecimento).

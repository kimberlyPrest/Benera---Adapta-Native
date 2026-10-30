# Benera Consultoria — Projeto Adapta Native

## Ritmo e teste do cliente

Vale desde 30/10/2026 e substitui o ritmo anterior, em que cada task fechava com autorização e teste humano próprios.
- Construa as tasks em sequência, uma por vez, sem pedir autorização nem teste entre elas. Cada task fecha pelas provas automáticas da SPEC (RED, GREEN, REGRESSÃO).
- O teste do cliente é por SPEC e segue a seção `## Teste humano do cliente` da SPEC da fase em execução.
- As Fases 1, 2 e 3 estão encerradas com aceite registrado e não são reabertas nem re-testadas; o ritmo novo vale a partir da próxima fase que for aberta.
- Continuam paradas: pergunta que muda implementação, acesso só do cliente, divergência que exige revisão e aprovação explícita exigida pela SPEC. Também permanecem as aprovações críticas quando houver mudança em dados, permissões ou fluxo já usado pela equipe, ou primeira gravação externa que não possa ser comprovada pelo agente e da qual as próximas tasks dependam. A regra de ritmo não dispensa autorização para integração externa nem para apagar ou reescrever dados reais. Preservar o aceite final da fase e todas as regras de segurança.

## Regras do projeto

Execute somente a fase atual e siga as SPECs e tasks publicadas. Não altere critérios de aceite sem aprovação da consultora.

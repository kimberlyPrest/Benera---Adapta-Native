# Constituição do projeto

- **Ponto focal (cliente):** Fábio Forcassin — valida processo e resultado; distribui a operação internamente.
- **Consultora:** Kim — define contrato, revisa segurança e libera fases; não substitui a decisão da Benera.
- **Stack permitida:** ambiente Skip, projeto 63138, para implementação/homologação da Fase 1, registrado por autorização de Kim em 02/10/2026. Esta decisão não presume migração, configuração de banco ou liberação de produção. O implementador confirma e documenta o runtime efetivo antes de aplicar alterações.
- **Linha vermelha:** nenhuma saída assistida vai ao cliente sem revisão humana; nenhuma fase avança sem evidências dos critérios de aceite; dados de clientes da Benera não saem do controle de acesso definido.
- **Acesso:** somente usuários convidados ou criados administrativamente; cadastro público não é permitido. Segredos nunca ficam em código, tela, fixture, log ou evidência.
- **Dívida:** registrar item, impacto, dono, prazo e fase de tratamento.

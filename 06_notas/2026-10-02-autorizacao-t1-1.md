# Autorização de implementação — T1.1

**Data:** 2026-10-02
**Autoridade:** Kim, consultora responsável
**Decisão na conversa:** “Pode registrar e liberar a task para implementar”.
**Task:** T1.1 — Implementar convite, login e perfis mínimos da Fase 1 com usuários sintéticos.
**Contrato:** `04_fase-atual/specs/spec-1-001.md`, CA-1-001 e CA-1-002.
**Estado:** AUTORIZADA PARA IMPLEMENTAÇÃO; não concluída nem homologada.

## Levantamento de entrada e limite da evidência

O levantamento apresentado à Kim informa Skip 63138, preview v0.0.1 sem publicação em produção, login/recuperação/verificação de e-mail existentes, convite e papéis ausentes e alteração pendente em `.skip.config.json`. Informa também criação pública na coleção users, ausência de campo de papel e credencial de demonstração embutida/exposta.

Esses pontos são registros do levantamento compartilhado, não resultados de nova inspeção do ambiente por esta publicação. O implementador deve confirmá-los antes de alterar código. A carcaça não é prova de conclusão da T1.1.

## Instrução ao implementador

1. Analisar a SPEC-1-001 e o ambiente real; preservar trabalho existente e alterações pendentes. Registrar o runtime e o estado inicial sem expor credenciais.
2. Disponibilizar fixture inteiramente sintética para u-admin/u-lead/u-consultor/u-reviewer; não usar dados reais de pessoas/clientes. Anexar o conteúdo da fixture ao dossiê, pois o caminho `05_execucao/fixtures/fase-1-fixtures.md` citado na SPEC pertence ao pacote do consultor e não está exportado neste repo.
3. Explicitar a matriz inicial dos quatro papéis conforme contratos existentes e submetê-la à validação operacional da Benera. Invariante já contratada: administrador configura; consultor não configura. Não inventar alçadas de líder/revisor nem liberar privilégios amplos por falta de definição. Enquanto a matriz não for validada, usar negação por padrão e não declarar CA-1-002 atendido.
4. Confirmar e fechar o cadastro público antes da homologação. Administrador cria convite com papel; se convite não for suportado, usar criação administrativa e registrar a limitação, como permite a SPEC. Não habilitar autoatribuição de papel pela pessoa convidada.
5. Invalidar/rotacionar a credencial de demonstração exposta, retirar o segredo de seed/tela/código e usar mecanismo seguro do runtime. Não basta esconder o texto na UI. Registrar somente confirmação sanitizada; nunca publicar o valor antigo ou novo.
6. Completar convite/ativação/login/perfis mínimos e reaproveitar autenticação existente apenas se compatível com o contrato. Recuperação/verificação de e-mail não substituem convite nem autorização.
7. Executar as provas abaixo e entregar checklist humano simples à Benera. Não marcar a task concluída sem aprovação humana.

## Provas para homologar T1.1

- Usuário sintético convidado ativa acesso e entra (CA-1-001).
- Administrador configura; consultor não configura, inclusive em tentativa direta ao servidor (CA-1-002).
- Cadastro anônimo é negado pelo servidor e não cria usuário.
- Credencial exposta deixa de autenticar; novo segredo não aparece em tela, código, fixture, log ou evidência.
- Convite expirado/duplicado/papel inválido não gera acesso indevido ou parcial.
- Build/testes do runtime executados e evidências sanitizadas anexadas com versão/commit.

## Fronteira com T1.2

A T1.2 continua responsável por isolamento por workspace/projeto, revogação e auditoria de acesso, com CA-1-003..006. Corrigir exposições básicas de cadastro/segredo é condição de homologação da T1.1, não substitui a execução nem o aceite integral da T1.2.

## Limites da liberação

- Autorizada a implementação da T1.1 e a preparação necessária de fixture/matriz no Skip 63138.
- Matriz ainda precisa de validação operacional; não há aceite inventado neste registro.
- Sem autorização de produção, uso de dados reais, encerramento da T1.1 ou avanço automático de fase.
- Esta decisão é documental: não executa mudanças no Skip, migrations, rotação de segredo, build ou testes.

# AP-2026-10-13-endpoints-agrupados — Promise.all com permissões diferentes derruba o carregamento

**Origem:** debug do dropdown vazio do consultor (T1.5/T1.6, Skip 63138) · **Data:** 2026-10-13

**Sinal:** consultor nunca viu etapas no dropdown; admin via tudo. `carregarEsteira()` agrupava /pipeline (200 p/ todos), /pipeline/versions (403 p/ consultor) e /priorities no mesmo Promise.all — o 403 rejeitava o lote inteiro.

**Aprendizado:** endpoints com permissões diferentes NÃO devem ser agrupados no mesmo Promise.all quando o resultado de um é essencial para papéis que não têm acesso ao outro. Carregar o que é universal em chamada separada.

**Regra aplicada (v0.0.33):** carregarEtapas() busca só pipeline+priorities; versões só na aba Esteira (admin).

**Reutilizável:** qualquer tela multi-papel.

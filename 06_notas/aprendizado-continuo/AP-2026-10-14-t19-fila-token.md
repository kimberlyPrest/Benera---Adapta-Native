# AP-2026-10-14-t19-fila-token — Fila/dado pessoal: filtro pelo token, nunca pela query

**Origem:** T1.9 (Skip 63138) · **Data:** 2026-10-14

**Sinal:** endpoint de fila individual (minhas-tarefas) precisava garantir que ninguém vê a fila de outro usuário.

**Aprendizado:** em endpoint que retorna dado pessoal operacional, o filtro de proprietário vem SEMPRE do token de autenticação (auth.id) — parâmetro de usuário na query é IGNORADO. Prova negativa: revisor consultando recebe só as próprias (zeradas), nunca as do consultor.

**Regra aplicada (v0.0.48, fila-listar.js).**

**Reutilizável:** qualquer "minhas X" no produto (fila, notificações, histórico pessoal).

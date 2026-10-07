# AP-2026-10-07-2030 — Query params e datas no runtime Skip (hooks PB)

**Origem:** T1.4 (Skip 63138) · **Data:** 2026-10-07

**Sinal:** hook de listagem quebrou com `TypeError: Cannot read property 'get' of undefined` (logs do servidor) ao usar `e.request.query` — não existe no runtime. `new DateTime()` também não está disponível no escopo JS dos hooks.

**Aprendizado (restrição de plataforma):**
- Query string em routerAdd: usar `e.request.url.query()` (API Go exposta ao JS) — `q.get('param')`.
- Datas para comparação: formatar string ISO no JS (`new Date().toISOString().replace('T',' ').slice(0,19) + '.000Z'`) e comparar lexicograficamente com `getDateTime(...).string()` — formato PB é estável ("2006-01-02 15:04:05.000Z").

**Reutilizável:** todo hook futuro que ler query params ou comparar datas.

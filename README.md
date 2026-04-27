# Calculadora de Aposentadoria — Renda Real (v2)

Calculadora de aposentadoria brasileira em arquivo HTML único, mobile-first, com projeções em termos reais (acima da inflação).

## v1 → v2: O que mudou

**v1** projetava o patrimônio futuro usando as taxas nominais de hoje (Selic 14,75%, etc.) como se persistissem por décadas. Isso superestimava retornos reais de longo prazo, já que taxas altas refletem ciclo monetário restritivo — não equilíbrio estrutural.

**v2** introduz um modelo de projeção com **taxas duráveis de longo prazo**:

- **Tesouro IPCA+ (mantido até o vencimento):** o spread real contratual É o retorno real de longo prazo. Está travado na compra. Aplica-se IR de 15% sobre o ganho real (aproximação conservadora).
- **Instrumentos pós-fixados (Selic, LCI/LCA, CDB):** convergem para a Selic real de longo prazo (default 4,5% a.a.), não para a Selic nominal de hoje.
- **Prefixado:** incluído na carteira com aviso de que é aposta direcional, não premissa estrutural.

### Novidades na interface

1. **Painel "Premissas de Longo Prazo"** — sliders para Selic real LP, IPCA LP e spread IPCA+.
2. **"Comparação de Cenários"** — mostra lado a lado:
   - "Se taxas atuais persistirem" (modelo v1, provavelmente otimista demais)
   - "Convergência ao equilíbrio" (modelo v2, recomendado)
3. **Carteira Sugerida** com duas colunas de taxa real líquida: "hoje" e "estrutural".

## Como usar

Abra `index.html` em qualquer navegador. Não requer servidor — funciona offline com dados fallback de abril/2026 e tenta buscar dados ao vivo do BCB e Tesouro Direto.

## Atualizar no GitHub Pages

Se já fez push do v1:

```bash
git add -A && git commit -m "v2 - durable long-term assumptions" && git push
```

## Stack

- HTML + CSS + JS vanilla, arquivo único
- Sem dependências externas
- APIs: BCB SGS, BCB Olinda Focus, Tesouro Direto JSON (best-effort, CORS)

## Disclaimer

Esta ferramenta é educacional. Não constitui recomendação de investimento. Consulte um profissional habilitado para decisões financeiras.

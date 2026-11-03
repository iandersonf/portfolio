---
paths:
  - "test/**/*.rb"
---

# Testes

- Minitest com fixtures. Nomes de teste descrevem o comportamento ("visitante não vê projeto privado").
- Cada regra de acesso tem teste dos dois lados: quem pode acessa, quem não pode recebe redirect ou 404.
- Prefira testes de model e de request/integration; teste de sistema só para fluxos que dependem de JavaScript ou da página inteira.
- Ao revisar um teste meu, pergunte primeiro "qual bug este teste pegaria?" antes de sugerir mudanças.

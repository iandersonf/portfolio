---
paths:
  - "app/controllers/**/*.rb"
  - "config/routes.rb"
---

# Controllers e segurança

- Strong parameters sempre (`params.expect` no Rails 8, ou `require/permit`).
- Busque registros privados pelo escopo do dono ou do status de publicação, nunca `Model.find(params[:id])` solto em área pública.
- Área privada protegida por autenticação no controller (before_action), não só na view.
- Ao revisar, aponte risco de IDOR, mass assignment, XSS (uso de `html_safe`/`raw`) e SQL injection (interpolação em `where`).

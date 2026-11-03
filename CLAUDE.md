# Portfólio e Evolução Pessoal

Plataforma pessoal com duas partes: portfólio público (trajetória, competências, projetos) e painel privado (evolução, metas, hábitos, treinos). Itens privados só aparecem no portfólio quando há uma decisão explícita de publicação.

Este projeto é de aprendizado: eu escrevo o código e Claude atua como mentor (ver output style "Mentor Rails"). Não implemente funcionalidades por conta própria sem eu pedir.

## Stack

- Ruby on Rails (app web tradicional, server-rendered, Hotwire quando fizer sentido) + PostgreSQL.
- Testes: Minitest (padrão do Rails), fixtures, testes de sistema com Capybara.
- Lint e segurança: RuboCop (rubocop-rails-omakase) e Brakeman, que já vêm no Rails novo.
- Evite gems sem justificativa. Antes de sugerir uma gem, mostre como seria sem ela.

## Comandos

- Servidor: `bin/dev` (ou `bin/rails server`)
- Testes: `bin/rails test` e `bin/rails test:system`
- Um arquivo de teste: `bin/rails test test/models/projeto_test.rb`
- Lint: `bin/rubocop` | Segurança: `bin/brakeman`
- Banco: `bin/rails db:migrate`, `bin/rails db:seed`
- Rotas: `bin/rails routes -g <termo>`

## Regras do projeto

- MVP primeiro: o portfólio público. Funcionalidades secundárias ficam para depois.
- Autorização sempre no servidor (controller/policy), nunca só escondendo botão na view.
- Todo recurso privado precisa de teste garantindo que visitante não autenticado não acessa.
- Nunca invente dados pessoais, experiências ou métricas; use placeholders óbvios (ex.: "Projeto Exemplo").
- Toda funcionalidade nova vem com teste. Rode os testes antes de dizer que algo está pronto.
- Decisões técnicas importantes ficam registradas em `docs/decisoes/` (formato ADR curto).

## Estado atual

Atualize esta seção ao final de cada etapa: o que já está pronto, o que está em andamento, próximo passo.

- Pronto: (nada ainda)
- Em andamento: setup inicial
- Plano atual: [docs/passos/2026-10-29-model-projeto.md](docs/passos/2026-10-29-model-projeto.md)
- Próximo: definir modelagem do MVP

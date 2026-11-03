# Passo: Model Projeto com publicação explícita
Status: em andamento
## Objetivo
Criar o model `Projeto` com o conceito de publicação embutido desde o início (escopo `publicados` e todo projeto nascendo privado), porque o projeto é o centro do portfólio público (MVP) e isso garante a regra "privado só aparece com decisão explícita" antes de existir qualquer página que possa vazar dados.
## Conceitos de Rails
- Generators: `rails generate model` cria migration, model, teste e fixture de uma vez (guia: The Rails Command Line → bin/rails generate)
- Migrations: mudanças no banco descritas em Ruby e versionadas; `null:` e `default:` protegem a regra no banco (guia: Active Record Migrations → Column Modifiers)
- Validations: regras de integridade no model, rodam antes de salvar (guia: Active Record Validations → presence)
- Scopes: consultas nomeadas e encadeáveis, como `Projeto.publicados` (guia: Active Record Query Interface → Scopes)
- Fixtures: dados de teste em YAML carregados em cada teste (guia: Testing Rails Applications → The Low-Down on Fixtures)
- Testes de model: testes unitários com Minitest (guia: Testing Rails Applications → Model Testing)
## Passos que eu executo
0. Fechar o setup: `bin/rails db:create`, `bin/rails test` (0 testes, sem erro), `bin/rubocop`, `bin/brakeman`; conferir que `config/master.key` está no `.gitignore`; fazer o primeiro commit.
1. `bin/rails generate model Projeto titulo:string descricao:text publicado:boolean` e observar os 4 arquivos gerados.
2. Antes de migrar, editar a migration: `titulo` com `null: false`; `publicado` com `default: false, null: false`.
3. `bin/rails db:migrate` e ler o `db/schema.rb` gerado.
4. Em `test/fixtures/projetos.yml`, criar duas fixtures com títulos placeholder: uma publicada ("Projeto Exemplo Publicado") e uma rascunho ("Projeto Exemplo Rascunho").
5. Escrever os testes em `test/models/projeto_test.rb` e rodar para ver falhar (ver "Primeiro teste").
6. Implementar a validação e o escopo no model até os testes passarem.
7. Registrar a decisão de publicação com `/decisao` e atualizar o "Estado atual" do CLAUDE.md.
## Primeiro teste
`Projeto.publicados` inclui a fixture publicada e não inclui a rascunho (deve falhar com `NoMethodError`). Em seguida: `Projeto.new` nasce com `publicado == false`; projeto sem título é inválido.
## Decisões pendentes
Idioma dos nomes: português (indicado pelo CLAUDE.md). Atenção: o inflector do Rails segue regras do inglês; palavras terminadas em "-ão" quebram ("decisao" → "decisaos") e exigem regra em `config/initializers/inflections.rb`.

Representação da publicação:
- A) `publicado:boolean` com default `false`: simples e explícito; não registra quando foi publicado.
- B) `publicado_em:datetime` (nulo = rascunho): permite ordenar e auditar; lógica um pouco menos óbvia (`where.not(publicado_em: nil)`).
- C) `enum :status` (rascunho/publicado/arquivado): flexível, mas resolve um problema que o MVP ainda não tem.

Recomendação: A. Suficiente para o MVP, e migrar para B ou C depois é uma migration simples. O essencial, nas três, é o default privado no banco.
## Critério de pronto
- `bin/rails test test/models/projeto_test.rb` verde com os 3 testes;
- `bin/rails test`, `bin/rubocop` e `bin/brakeman` limpos;
- ADR da decisão de publicação em `docs/decisoes/`;
- "Estado atual" do CLAUDE.md atualizado.
## Notas

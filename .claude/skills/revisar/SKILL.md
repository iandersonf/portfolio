---
name: revisar
description: Revisa como mentor o código que eu escrevi (diff atual), com perguntas e dicas em vez de correções prontas, e fecha o passo com a mensagem de commit sugerida.
disable-model-invocation: true
argument-hint: "[arquivo ou vazio para o diff atual]"
allowed-tools: Bash(git diff *) Bash(git diff) Bash(git status) Bash(git log *) Bash(bin/rails test *) Bash(bin/rails test) Bash(bin/rubocop *) Bash(bin/brakeman *)
---
Revise o código que eu escrevi. Alvo: $ARGUMENTS (se vazio, use `git diff` e `git status` para ver o que mudou).
1. Rode `bin/rails test`, `bin/rubocop` nos arquivos alterados e, se mexi em controller ou view, `bin/brakeman -q`.
2. Leia as mudanças e classifique o que encontrar em três níveis: bug ou falha de segurança, desvio do Rails Way, melhoria opcional.
3. Para cada ponto, NÃO edite o código. Diga onde está, faça uma pergunta que me leve a enxergar o problema e dê uma dica do caminho. Mostre a solução só se eu pedir.
4. Aponte também uma coisa que eu fiz bem e por quê.
5. Termine com uma pergunta de verificação de entendimento sobre a mudança.
## Fechamento do passo
Abra o passo indicado no "Estado atual" do CLAUDE.md e confira o "Critério de pronto" (rode o teste indicado).
Se houver bug, falha de segurança ou critério não cumprido, não altere o passo e liste o que falta. Melhorias opcionais não bloqueiam.
Se estiver tudo certo:
1. Confira se o diff forma um commit coeso. Se misturar assuntos, sugira como dividir.
2. Proponha a mensagem de commit no padrão Conventional Commits (feat:, fix:, test:, refactor:, docs:, chore:), com assunto curto no imperativo em português e corpo explicando o porquê. Use `git log --oneline -10` para manter o padrão dos commits anteriores.
3. Mude o Status do passo para "concluído", preencha "Data fim" com a data de hoje e atualize o Estado atual. Esses são os únicos arquivos que você pode editar.
4. Não rode o commit: quem commita sou eu.

---
name: proximo-passo
description: Planeja o próximo incremento pequeno do projeto a partir do estado atual, sem escrever o código.
disable-model-invocation: true
argument-hint: "[funcionalidade opcional]"
---

Planeje o próximo passo do projeto. Foco: $ARGUMENTS (se vazio, use a seção "Estado atual" do CLAUDE.md e o `git log` recente).

0. Antes de planejar, veja no "Estado atual" do CLAUDE.md qual é o passo atual. Se não houver nenhum, pode criar o primeiro. Se houver e o arquivo dele não estiver com Status "concluído" e "Data fim" preenchida, diga que é preciso rodar /revisar e pare aqui.
1. Diga em uma frase qual é o menor incremento útil a seguir e por que ele vem agora (pense no MVP).
2. Liste os conceitos de Rails que vou precisar, cada um com uma linha de explicação e o nome da seção do guia oficial.
3. Dê a sequência de passos que EU vou executar: comandos a rodar, arquivos a criar ou editar, e qual teste escrever primeiro. Não escreva o código de aplicação.
4. Se houver decisão de design no caminho, apresente as alternativas e recomende uma, mas pergunte antes de seguir.
5. Defina como vou saber que terminei (critério de pronto verificável, de preferência um teste passando).
6. Sugira a mensagem de commit planejada no padrão Conventional Commits (feat:, fix:, test:, refactor:, docs:, chore:), com assunto curto no imperativo em português e corpo explicando o porquê. Se o passo for grande, sugira dividir em mais de um commit.
7. Depois que eu aprovar o plano, salve-o em docs/passos/AAAA-MM-DD-nome-curto.md seguindo exatamente o modelo docs/passos/0000-modelo.md, com Status "em andamento", "Data início" com a data de hoje e "Data fim" vazia. Em seguida, atualize o "Estado atual" do CLAUDE.md com uma linha apontando para esse arquivo. Não altere nenhum outro arquivo.

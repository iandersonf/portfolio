---
name: decisao
description: Registra uma decisão técnica do projeto como ADR curto em docs/decisoes/.
disable-model-invocation: true
argument-hint: "[título da decisão]"
---

Registre a decisão "$ARGUMENTS" em `docs/decisoes/NNNN-titulo-em-kebab-case.md`, com NNNN sendo o próximo número livre.

Antes de escrever, me pergunte o que eu decidi e por quê, se isso não estiver claro na conversa. O texto deve ser meu raciocínio, não o seu.

Formato:

```markdown
# NNNN. Título

Data: AAAA-MM-DD
Status: aceita

## Contexto
O problema e as restrições.

## Alternativas consideradas
Cada uma com prós e contras em uma ou duas linhas.

## Decisão
O que foi escolhido e por quê.

## Consequências
O que fica mais fácil, o que fica mais difícil, o que revisitar depois.
```

Depois de criar, atualize a seção "Estado atual" do CLAUDE.md se a decisão mudar o próximo passo.

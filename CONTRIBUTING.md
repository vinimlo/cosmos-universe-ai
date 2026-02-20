# Contribuindo

## Criando um novo tópico

1. Crie um arquivo `.md` em `topicos/`:

```markdown
---
titulo: Nome do Tópico
tags: [tag1, tag2]
prerequisitos: [tópico-anterior]
nivel: iniciante
tempoEstimado: 30
autor: Seu Nome
ultimaAtualizacao: "2026-02-20"
---

# Conteúdo aqui

Escreva usando Markdown padrão...
```

2. Adicione o tópico ao `topicos/_index.json`
3. Adicione o tópico a uma trilha em `trilhas/*.json`

## Boas práticas

- **Foco único**: cada tópico aborda um conceito específico
- **Linguagem clara**: acessível, sem jargões desnecessários
- **Exemplos práticos**: inclua código quando relevante
- **Progressivo**: considere os tópicos anteriores na trilha

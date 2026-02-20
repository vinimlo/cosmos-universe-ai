# Cosmos Universe AI

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Topicos](https://img.shields.io/badge/T%C3%B3picos-44%2B-6366f1.svg)](#trilhas-disponiveis)
[![Trilhas](https://img.shields.io/badge/Trilhas-3-10b981.svg)](#trilhas-disponiveis)

> Conteudo de Inteligencia Artificial no formato Universe para o Cosmos.

<!-- TODO: Adicionar screenshot do site gerado -->
<!-- ![Screenshot](docs/screenshot.png) -->

## O que e?

Um pack de conteudo educacional sobre **Inteligencia Artificial e Machine Learning**, estruturado no formato [Universe](https://github.com/vinimlo/cosmos). Quando combinado com o [Cosmos](https://github.com/vinimlo/cosmos), gera um site de aprendizado gamificado completo com trilhas, progresso e conquistas.

Todo o conteudo esta em **portugues brasileiro** (pt-BR).

## Trilhas Disponiveis

### LLM do Zero

Entenda como LLMs funcionam por dentro, construindo um do zero.

- 9 topicos em 3 modulos
- Nivel: Intermediario
- Fundamentos matematicos, arquitetura Transformer, construindo seu GPT

### IA Pratica

Aplique IA em projetos reais: LLMs, RAG, agentes e integracoes.

- 33 topicos em 10 modulos
- Nivel: Intermediario
- Prompt Engineering, APIs, embeddings, vector databases, RAG, agentes, multimodal

### AI Engineer

Torne-se um engenheiro de IA completo, dominando LLMs, RAG, agentes e muito mais.

- 35 topicos em 10 modulos
- Nivel: Intermediario
- Roadmap completo desde fundamentos ate agentes autonomos

## Como Usar

### Com o Cosmos (recomendado)

A forma mais facil e usando o repositorio integrador [GAEIA](https://github.com/vinimlo/GAEIA):

```bash
git clone --recursive https://github.com/vinimlo/GAEIA.git
cd GAEIA
docker compose up
# Acesse http://localhost:4321
```

### Como conteudo standalone

O conteudo sao arquivos Markdown com frontmatter YAML — podem ser lidos diretamente no GitHub, em qualquer editor Markdown, ou no [Obsidian](https://obsidian.md).

```bash
git clone https://github.com/vinimlo/cosmos-universe-ai.git
# Abra a pasta no seu editor favorito ou no Obsidian
```

## Estrutura

```
universe/
├── _catalog.json           # Catalogo raiz (nome, branding, trilhas)
├── trilhas/                # Trilhas de aprendizado (JSON)
│   ├── llm-do-zero.json    # LLM do Zero
│   ├── ia-pratica.json     # IA Pratica
│   └── ai-engineer.json    # AI Engineer
├── topicos/                # Conteudo atomico (Markdown)
│   ├── _index.json         # Indice de topicos
│   ├── llms-intro.md
│   ├── embeddings-intro.md
│   └── ... (44+ topicos)
└── shared/                 # Assets compartilhados
    └── logo.svg
```

## Contribuindo com Conteudo

### Criando um novo topico

1. Crie um arquivo `.md` em `topicos/`:

```markdown
---
titulo: Nome do Topico
tags: [tag1, tag2]
prerequisitos: [topico-anterior]
nivel: iniciante
tempoEstimado: 30
autor: Seu Nome
ultimaAtualizacao: "2026-02-19"
---

# Conteudo aqui

Escreva usando Markdown padrao...
```

2. Adicione o topico ao `topicos/_index.json`
3. Adicione o topico a uma trilha em `trilhas/*.json`

### Boas praticas

- **Foco unico**: cada topico aborda um conceito especifico
- **Linguagem clara**: acessivel, sem jargoes desnecessarios
- **Exemplos praticos**: inclua codigo quando relevante
- **Progressivo**: considere os topicos anteriores na trilha

## Acesse Online

Acesse o conteudo no site: [vinimlo.github.io/gaeia](https://vinimlo.github.io/gaeia)

## Licenca

Este projeto esta licenciado sob a [MIT License](LICENSE).

---

Feito para a comunidade de IA brasileira.

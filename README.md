# Cosmos Universe AI

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](LICENSE)
[![Topicos](https://img.shields.io/badge/T%C3%B3picos-44%2B-6366f1.svg)](#trilhas)
[![Trilhas](https://img.shields.io/badge/Trilhas-3-10b981.svg)](#trilhas)

Conteúdo educacional de Inteligência Artificial em português brasileiro, estruturado como um [Universe](https://github.com/vinimlo/cosmos) para o [Cosmos](https://github.com/vinimlo/cosmos).

## Quickstart

```bash
git clone --recursive https://github.com/vinimlo/GAEIA.git
cd GAEIA
docker compose up
# http://localhost:4321
```

Ou acesse direto em [vinimlo.github.io/gaeia](https://vinimlo.github.io/gaeia).

## Trilhas

| Trilha | Tópicos | Nível | Foco |
|--------|---------|-------|------|
| **LLM do Zero** | 9 em 3 módulos | Intermediário | Fundamentos matemáticos, arquitetura Transformer, construindo um GPT |
| **IA Prática** | 33 em 10 módulos | Intermediário | Prompt engineering, APIs, embeddings, RAG, agentes |
| **AI Engineer (roadmap.sh)** | 35 em 10 módulos | Intermediário | Roadmap de fundamentos até agentes autônomos |

## Uso standalone

O conteúdo são arquivos Markdown com frontmatter YAML. Funcionam direto no GitHub, em qualquer editor, ou no [Obsidian](https://obsidian.md).

```bash
git clone https://github.com/vinimlo/cosmos-universe-ai.git
```

## Estrutura

```
universe/
├── _catalog.json           # Catálogo raiz (nome, branding, trilhas)
├── trilhas/                # Trilhas de aprendizado (JSON)
│   ├── llm-do-zero.json
│   ├── ia-pratica.json
│   └── ai-engineer.json
├── topicos/                # Conteúdo atômico (Markdown)
│   ├── _index.json         # Índice de tópicos
│   └── ... (44+ tópicos)
└── shared/                 # Assets compartilhados
    └── logo.svg
```

## Licença

[CC BY-SA 4.0](LICENSE)

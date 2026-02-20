---
titulo: "Tokenização"
tags: ["nlp", "pré-processamento", "bpe", "texto", "vocabulário"]
prerequisitos: ["backpropagation"]
nivel: "intermediario"
tempoEstimado: 120
autor: "GAEIA"
ultimaAtualizacao: "2026-02-03"
---

# Tokenização

**Teoria:** BPE (Byte Pair Encoding), vocabulário, tokens vs caracteres

**Prática:** Implementar tokenizer BPE do zero

> Antes de transformar texto em vetores, precisamos decidir: qual a unidade básica? Caractere? Palavra? A resposta é mais sutil do que parece.

---

## Papers Fundamentais

- **Sennrich, Haddow & Birch (2016) - BPE for NMT** - Adaptação do algoritmo de compressão para tradução
  - [arxiv.org/abs/1508.07909](https://arxiv.org/abs/1508.07909)

- **Kudo & Richardson (2018) - SentencePiece** - Tokenização language-independent, sem pré-tokenização
  - [arxiv.org/abs/1808.06226](https://arxiv.org/abs/1808.06226)

- **Kudo (2018) - Unigram Model** - Alternativa ao BPE: começa grande e trima por loss
  - [arxiv.org/abs/1804.10959](https://arxiv.org/abs/1804.10959)

---

## Vídeos e Tutoriais

- **Karpathy - Let's build the GPT Tokenizer** - Vídeo dedicado só à tokenização
  - [youtube.com/watch?v=zduSFxRajkE](https://youtube.com/watch?v=zduSFxRajkE)

- **HuggingFace LLM Course - BPE Chapter** - Implementação pedagógica completa
  - [huggingface.co/learn/llm-course/en/chapter6/5](https://huggingface.co/learn/llm-course/en/chapter6/5)

- **Sebastian Raschka - BPE From Scratch** - Jupyter notebook standalone imitando tiktoken
  - [sebastianraschka.com/blog/2025/bpe-from-scratch.html](https://sebastianraschka.com/blog/2025/bpe-from-scratch.html)

---

## Código de Referência

- **Karpathy - minbpe** - Implementação educacional de referência: BasicTokenizer, RegexTokenizer (GPT-2), GPT4Tokenizer
  - [github.com/karpathy/minbpe](https://github.com/karpathy/minbpe)
  - Inclui `exercise.md` para prática hands-on

- **HuggingFace Tokenizers Summary** - Comparação BPE vs WordPiece vs Unigram
  - [huggingface.co/docs/transformers/en/tokenizer_summary](https://huggingface.co/docs/transformers/en/tokenizer_summary)

- **rsennrich/subword-nmt** - Implementação original dos autores do paper
  - [github.com/rsennrich/subword-nmt](https://github.com/rsennrich/subword-nmt)

---

## Comparação de Métodos

| Método | Usado por | Estratégia |
|--------|-----------|------------|
| **BPE** | GPT-2, GPT-4, LLaMA | Merge pares mais frequentes |
| **WordPiece** | BERT | Merge pares que maximizam likelihood |
| **Unigram** | XLNet, T5 | Começa grande, trima por loss |
| **SentencePiece** | T5, LLaMA | Wrapper language-independent |

---

## Entregável

Tokenizer BPE treinado em Tiny Shakespeare com vocabulário de 256 tokens.

**Round-trip test:** `decode(encode(texto)) == texto` para qualquer string do corpus.

**Métrica:** Calcule a taxa de compressão `(chars / tokens)` — deve ser > 2x.

**Você deve conseguir explicar:** Por que tokens BPE são melhores que caracteres individuais e melhores que palavras inteiras.

---

## Checklist

- [ ] Assistir Karpathy GPT Tokenizer
- [ ] Ler sobre BPE
- [ ] Entender diferença entre métodos
- [ ] Implementar BPE do zero
- [ ] Treinar em um corpus
- [ ] Testar encode/decode

---

## Conexões

> **Fundamento:** Este tópico usa conceitos de [[backpropagation]]
>
> **Próximo passo:** Aprenda como tokens viram vetores em [[embeddings-texto]]

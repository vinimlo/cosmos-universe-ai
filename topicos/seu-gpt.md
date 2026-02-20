---
titulo: "Seu GPT"
tags: ["projeto", "gpt", "transformer", "implementação", "decoder-only", "autoregressive"]
prerequisitos: ["transformer", "tokenizacao"]
nivel: "avançado"
tempoEstimado: 300
autor: "GAEIA"
ultimaAtualizacao: "2026-02-03"
---

# Seu GPT (Entregável Final)

**Teoria:** Decoder-only architecture, autoregressive generation

**Prática:** Juntar tokenizer + transformer blocks + training loop + geração

---

## Papers Fundamentais

- **GPT-1 (2018) - "Improving Language Understanding by Generative Pre-Training"** - 12 layers, 768 dims, 12 heads, ~117M params
  - [cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf)

- **GPT-2 (2019) - "Language Models are Unsupervised Multitask Learners"** - Byte-level BPE, pre-LayerNorm
  - [cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)

---

## Implementações de Referência

- **Karpathy - nanoGPT** - ~600 linhas que reproduzem GPT-2 (124M) no OpenWebText. Custo: ~$10 e ~1h no Lambda Labs
  - [github.com/karpathy/nanoGPT](https://github.com/karpathy/nanoGPT)

- **Karpathy - build-nanogpt** - Vídeo de 4h + commits limpos para acompanhar passo a passo
  - [github.com/karpathy/build-nanogpt](https://github.com/karpathy/build-nanogpt)

- **jaymody/picoGPT** - Forward pass em 40 linhas de NumPy - inferência com pesos reais do GPT-2
  - [github.com/jaymody/picoGPT](https://github.com/jaymody/picoGPT)

---

## Hyperparameters de Referência (nanoGPT 124M)

| Parâmetro | Valor | O que faz |
|-----------|-------|-----------|
| **Learning rate** | 6e-4 | Tamanho do passo de atualização dos pesos. Muito alto = diverge, muito baixo = lento |
| **Weight decay** | 0.1 | Penaliza pesos grandes para evitar overfitting (multiplica pesos por 0.999 cada step) |
| **Warmup** | Linear → cosine decay to 10% | Começa com lr baixo, sobe linearmente, depois decai suavemente até 10% do pico |
| **Dropout** | 0.1 | Desliga 10% dos neurônios aleatoriamente durante treino, forçando redundância |
| **Activation** | GELU | Versão suave do ReLU (você viu em [[mlp-e-matrizes]]) |
| **Position embeddings** | Learned | Vetores aprendidos (não sinusoidais) indicando posição de cada token |

---

## Apple Silicon (MLX)

- **MLX Framework**
  - [github.com/ml-explore/mlx](https://github.com/ml-explore/mlx)
  - [ml-explore.github.io/mlx](https://ml-explore.github.io/mlx)

- **nanoGPT_mlx** - Port direto do nanoGPT para MLX
  - [github.com/vithursant/nanoGPT_mlx](https://github.com/vithursant/nanoGPT_mlx)

---

## Datasets para Treino

| Dataset | Tamanho | Ideal para |
|---------|---------|------------|
| **Tiny Shakespeare** | ~1MB | Experimentos rápidos (incluso no nanoGPT) |
| **TinyStories** | 2.14M histórias | Modelos coerentes < 10M params em < 1 dia |

- [huggingface.co/datasets/roneneldan/TinyStories](https://huggingface.co/datasets/roneneldan/TinyStories)

---

## Entregável Final

**Marco intermediário (antes de treinar):** Faça um forward pass com input aleatório. Verifique que o loss inicial é `~ln(vocab_size)` (distribuição uniforme sobre o vocabulário).

**Montagem passo a passo:**
1. Use seu tokenizer (tópico 6) para processar Tiny Shakespeare
2. Use seus blocos Transformer (tópico 8) empilhados com embedding + head
3. Adapte seu training loop (tópico 4) para PyTorch com AdamW
4. Implemente geração autoregressiva (novo)
5. Treine e avalie

### Tier 1 - Laptop (sem GPU dedicada)
GPT **character-level**, ~1M parâmetros. Após 5000 iterações, deve gerar texto com palavras reconhecíveis em inglês.

### Tier 2 - Com GPU
GPT **token-level** (BPE), ~10-30M parâmetros. Após treinamento completo, deve gerar histórias de 3-5 frases com coerência gramatical.

**Você deve conseguir explicar:** Por que o loss inicial deveria ser aproximadamente `ln(vocab_size)`.

---

## Guia de Hardware e Setup

**Setup PyTorch:**
- **NVIDIA GPU:** `pip install torch` (CUDA já incluso nas builds oficiais)
- **Apple Silicon:** `pip install torch` (suporte MPS automático desde PyTorch 2.0)
- **CPU only:** Funciona, mas só viável para Tier 1

**Tempos estimados de treino:**

| Hardware | Tier 1 (~1M params) | Tier 2 (~10-30M params) |
|----------|---------------------|------------------------|
| MacBook M1/M2 (MPS) | ~5 min | ~3-6h |
| NVIDIA RTX 3090/4090 | ~2 min | ~1-2h |
| Google Colab (T4 free) | ~5 min | ~4-8h |

**Opções cloud (se não tem GPU):**
- **Google Colab** - Gratuito com T4, suficiente para Tier 2
- **Lambda Labs** - ~$1/hr para uma A10G, treina Tier 2 em ~1h

---

## Checklist

- [ ] Revisar tópicos anteriores
- [ ] Configurar ambiente PyTorch/MLX
- [ ] Integrar tokenizer + transformer
- [ ] Implementar training loop
- [ ] Escolher dataset e tier
- [ ] Treinar modelo
- [ ] Implementar geração de texto
- [ ] Avaliar qualidade do texto gerado

---

## Conclusão

**Você construiu um GPT.** De um único neurônio com dot product até um transformer autoregressivo que gera texto - cada peça foi implementada e entendida por você.

### Próximos passos sugeridos:
- **Fine-tuning:** Adapte seu modelo para uma tarefa específica
- **Scaling:** Experimente aumentar layers, heads, dimensão - observe o que muda
- **Leia GPT-3/LLaMA papers:** Agora você tem vocabulário para entender as decisões de design
- **RLHF/DPO:** Entenda como modelos são alinhados após o pré-treino

---

## Conexões

> **Fundamento:** Este tópico integra [[transformer]] e [[tokenizacao]]
>
> **Parabéns!** Você completou a trilha LLM do Zero!

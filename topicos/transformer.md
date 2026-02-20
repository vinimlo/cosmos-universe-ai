---
titulo: "Transformer Completo"
tags: ["transformer", "arquitetura", "nlp", "encoder-decoder", "multi-head-attention", "layer-norm", "feed-forward"]
prerequisitos: ["self-attention"]
nivel: "avançado"
tempoEstimado: 300
autor: "GAEIA"
ultimaAtualizacao: "2026-02-03"
---

# O Transformer Completo

**Teoria:** Multi-head attention, layer norm, residual connections, positional encoding, feed-forward sublayer

**Prática:** Montar um bloco Transformer completo

> Cada componente é simples isolado. A arquitetura é a composição deles.

---

## Papers Originais dos Componentes

- **Ba, Kiros & Hinton (2016) - Layer Normalization** - Normaliza por features (não batch), consistente em train/test
  - [arxiv.org/abs/1607.06450](https://arxiv.org/abs/1607.06450)

- **He et al. (2016) - Deep Residual Learning (ResNet)** - Skip connections que permitiram treinar 152+ camadas
  - [arxiv.org/abs/1512.03385](https://arxiv.org/abs/1512.03385)

---

## Implementações Anotadas

- **Harvard NLP - The Annotated Transformer** - ~400 linhas de PyTorch intercaladas com texto do paper, Jupyter notebook executável (atualizado 2022)
  - [nlp.seas.harvard.edu/annotated-transformer](https://nlp.seas.harvard.edu/annotated-transformer)
  - [github.com/harvardnlp/annotated-transformer](https://github.com/harvardnlp/annotated-transformer)

- **Karpathy - build-nanogpt** - Vídeo de 4h construindo GPT-2 de um arquivo vazio, commits limpos
  - [github.com/karpathy/build-nanogpt](https://github.com/karpathy/build-nanogpt)

- **Karpathy - minGPT** - 3 arquivos, prioriza educação sobre performance
  - [github.com/karpathy/minGPT](https://github.com/karpathy/minGPT)

- **Dive into Deep Learning - Attention Mechanisms** - Multi-framework (PyTorch, JAX, TF)
  - [d2l.ai/chapter_attention-mechanisms-and-transformers](https://d2l.ai/chapter_attention-mechanisms-and-transformers)

---

## Positional Encoding Deep Dive

- **Amirhossein Kazemnejad** - Explicação mais profunda de por que funções sinusoidais funcionam, com interpretação geométrica
  - [kazemnejad.com/blog/transformer_architecture_positional_encoding](https://kazemnejad.com/blog/transformer_architecture_positional_encoding)
  - Propriedades chave:
    - Generaliza para sequências maiores que o treino
    - Dot products refletem distância relativa
    - Dimensões baixas capturam estrutura global

---

## Feed-Forward Sublayer

Cada bloco Transformer tem dois sublayers: **attention** e **feed-forward**. O feed-forward é surpreendentemente simples:

```
FFN(x) = Linear(GELU(Linear(x)))
```

A primeira camada linear expande a dimensão por um fator de **4x** (ex: 768 → 3072), aplica uma ativação (GELU nos GPTs), e a segunda camada projeta de volta para a dimensão original (3072 → 768).

Por que expandir e comprimir? A attention captura *relações entre tokens*. O feed-forward processa cada token *individualmente*, dando à rede capacidade de transformar representações. Pesquisas recentes sugerem que os feed-forward layers funcionam como "memórias" que armazenam conhecimento factual.

---

## Insight Chave

**Residual connections são o que tornam redes profundas possíveis.** Ao somar `x + sublayer(x)` ao invés de só `sublayer(x)`, você cria um "atalho" para os gradientes fluírem direto até as primeiras camadas. Sem isso, gradientes morrem exponencialmente com a profundidade. Layer norm estabiliza as magnitudes em cada camada. Juntos, eles permitem empilhar dezenas (ou centenas) de blocos Transformer.

---

## Entregável

Um bloco Transformer em **PyTorch** (`nn.Module`) com: 4 cabeças de atenção, dimensão 64, feed-forward de 256. Este é o momento de migrar para PyTorch.

**Teste de shapes:** Input `(batch=2, seq=8, dim=64)` → output deve ter o mesmo shape.

**Teste de corretude:** Compare a saída do seu bloco com `nn.TransformerEncoderLayer` do PyTorch usando os mesmos pesos. Diferença deve ser `< 1e-5`.

**Smoke test:** Empilhe 2 blocos, conecte com embedding layer + linear head, faça um forward pass no Tiny Shakespeare. Não precisa treinar — só verificar que os tensores fluem.

**Você deve conseguir explicar:** O que acontece com os gradientes sem residual connections.

---

## Checklist

- [ ] Entender multi-head attention
- [ ] Implementar layer normalization
- [ ] Implementar residual connections
- [ ] Implementar positional encoding
- [ ] Implementar feed-forward sublayer
- [ ] Montar bloco transformer completo
- [ ] Testar com sequências de exemplo

---

## Conexões

> **Fundamento:** Este tópico usa conceitos de [[self-attention]]
>
> **Próximo passo:** Integre tudo em [[seu-gpt]]

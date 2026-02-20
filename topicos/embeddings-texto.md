---
titulo: "Embeddings de Texto"
tags: ["nlp", "vetores", "representação", "word2vec", "embeddings"]
prerequisitos: ["tokenizacao"]
nivel: "intermediario"
tempoEstimado: 240
autor: "GAEIA"
ultimaAtualizacao: "2026-02-03"
---

# Embeddings e Representação de Texto

**Teoria:** Palavras como vetores, one-hot encoding, embeddings como lookup tables

**Prática:** Implementar embedding layer, alimentar MLP com texto

> A ponte entre "rede neural genérica" e "modelo de linguagem". Aqui você começa a ver como texto vira números.

---

## A Grande Transição: de XOR para Linguagem

Até agora, você construiu uma MLP que aprende patterns como XOR. Um **modelo de linguagem** faz algo conceitualmente similar, mas com texto: dada uma sequência de palavras, ele prevê a próxima. Formalmente: `P(proxima_palavra | palavras_anteriores)`.

Para fazer isso, precisamos resolver um problema fundamental: redes neurais operam com números, mas texto é simbólico. **Embeddings** são a solução - vetores densos que capturam significado, onde palavras similares ficam próximas no espaço vetorial. Diferente de one-hot (esparso, sem relação entre palavras), embeddings são *aprendidos* junto com o modelo.

---

## Vídeos Fundamentais

- **Karpathy - makemore (bigram language model)** - Segundo vídeo da série Zero to Hero
  - [youtube.com/watch?v=PaCmpygFfXo](https://youtube.com/watch?v=PaCmpygFfXo)

- **Karpathy - makemore part 3 (MLP language model)** - Ponte direta entre a MLP que você construiu e language modeling. Implementa Bengio et al. (2003)
  - [youtube.com/watch?v=TCH_1BHY58I](https://youtube.com/watch?v=TCH_1BHY58I)

---

## Papers Fundamentais

- **Mikolov et al. (2013) - Word2Vec** - Paper original: Skip-gram e CBOW
  - [arxiv.org/abs/1301.3781](https://arxiv.org/abs/1301.3781)

- **Goldberg & Levy - word2vec Explained** - Clareza matemática que o paper original não tem
  - [arxiv.org/abs/1402.3722](https://arxiv.org/abs/1402.3722)

- **Rong - word2vec Parameter Learning Explained** - Detalhamento completo do aprendizado
  - [arxiv.org/abs/1411.2738](https://arxiv.org/abs/1411.2738)

- **Pennington, Socher & Manning (2014) - GloVe** - Combina co-ocorrência global com contexto local
  - [nlp.stanford.edu/projects/glove](https://nlp.stanford.edu/projects/glove)

- **Bengio (2003) - A Neural Probabilistic Language Model** - O paper que inaugurou embeddings aprendidos e LMs neurais
  - [jmlr.org/papers/v3/bengio03a.html](https://jmlr.org/papers/v3/bengio03a.html)

---

## Leituras e Tutoriais

- **Jay Alammar - The Illustrated Word2Vec** - Visualizações excepcionais de CBOW e Skip-gram
  - [jalammar.github.io/illustrated-word2vec](https://jalammar.github.io/illustrated-word2vec)

- **Analytics Vidhya - From Count Vectors to Word2Vec** - Progressão de one-hot -> TF-IDF -> embeddings neurais
  - [analyticsvidhya.com/blog/2017/06/word-embeddings-count-word2veec](https://analyticsvidhya.com/blog/2017/06/word-embeddings-count-word2veec)

---

## Ferramentas de Visualização

- **TensorFlow Embedding Projector** - Exploração 3D interativa com PCA, t-SNE, UMAP
  - [projector.tensorflow.org](https://projector.tensorflow.org)

- **gpt-intuition** - Alternativa Streamlit mais fácil de configurar
  - [github.com/epec254/gpt-intuition](https://github.com/epec254/gpt-intuition)

---

## Insight Chave

**Uma embedding layer é "só" uma lookup table treinável.** Internamente, é uma multiplicação de matriz com um vetor one-hot - mas como one-hot tem um único 1, isso equivale a selecionar uma linha da matriz. Essa matriz de embeddings é aprendida junto com o resto da rede via backprop. O resultado: palavras que aparecem em contextos similares acabam com vetores similares, sem ninguem programar isso explicitamente.

---

## Entregável

**Etapa 1:** Implemente um bigram character-level **sem embeddings** (tabela de contagem + probabilidades). Treine num texto curto (~100KB). Gere 200 caracteres — deve parecer aleatório mas respeitar frequências de pares.

**Etapa 2:** Substitua a tabela de contagem pelo seu MLP: cada caractere vira um embedding vector de dimensão 8, janela de contexto de 2 caracteres, saída via softmax sobre o vocabulário. Treine e compare com o bigram de contagem.

**Verificação:** Gere 200 caracteres com o modelo neural. Deve produzir sequências que lembram palavras (não precisa fazer sentido, mas deve parecer quase-linguagem).

**Você deve conseguir explicar:** Por que uma embedding layer é "só" uma lookup table treinável.

---

## Checklist

- [ ] Assistir Karpathy makemore (bigram)
- [ ] Assistir Karpathy makemore part 3 (MLP)
- [ ] Ler Jay Alammar sobre Word2Vec
- [ ] Entender one-hot vs embeddings
- [ ] Implementar embedding layer
- [ ] Treinar modelo bigram/trigram
- [ ] Gerar texto simples

---

## Conexões

> **Fundamento:** Este tópico usa conceitos de [[tokenizacao]]
>
> **Na prática:** Embeddings são essenciais para RAG e busca semântica
>
> **Próximo passo:** Entenda como tokens prestam atenção uns nos outros em [[self-attention]]

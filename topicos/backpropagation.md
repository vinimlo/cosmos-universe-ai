---
titulo: "Backpropagation"
tags: ["fundamentos", "neural", "gradientes", "otimização", "regra-da-cadeia", "computational-graph"]
prerequisitos: ["loss-e-derivadas"]
nivel: "intermediario"
tempoEstimado: 420
autor: "GAEIA"
ultimaAtualizacao: "2026-02-03"
---

# Backpropagation (Marco Crítico)

**Teoria:** Regra da cadeia em profundidade, derivadas parciais, computational graph, otimizadores

**Prática:** Implementar backprop na mão para seu MLP

> **Esse é o tópico mais denso. Não apresse.** A regra da cadeia é *a essência* de como redes neurais aprendem.

---

## Vídeos Fundamentais

- **Karpathy - micrograd (vídeo completo)** - Autograd engine do zero, 2h30 de ouro puro (assista o vídeo COMPLETO desta vez - você viu o início em [[neuronio-e-vetores]])
  - [youtube.com/watch?v=VMj-3S1tku0](https://youtube.com/watch?v=VMj-3S1tku0)

- **3Blue1Brown - Backpropagation** - Visualização da propagação de gradientes
  - [3blue1brown.com/lessons/backpropagation](https://3blue1brown.com/lessons/backpropagation)

---

## Leituras e Tutoriais

- **CS231n - Backpropagation Notes** - Backprop como "backward flow in real-valued circuits", gate communication (add distributes, multiply swaps)
  - [cs231n.github.io/optimization-2](https://cs231n.github.io/optimization-2)

- **CS231n - Optimization Notes** - Gradient descent, learning rate, SGD, momentum, Adam - tudo que falta entre "calcular gradiente" e "atualizar pesos"
  - [cs231n.github.io/neural-networks-3](https://cs231n.github.io/neural-networks-3)

- **Colah - Calculus on Computational Graphs** - Diagramas excelentes de forward e reverse-mode differentiation
  - [colah.github.io/posts/2015-08-Backprop](https://colah.github.io/posts/2015-08-Backprop)

- **Rumelhart, Hinton & Williams (1986)** - Paper original de backpropagation na Nature (3 páginas históricas)
  - [nature.com/articles/323533a0](https://nature.com/articles/323533a0)

---

## Exercícios de Cálculo Manual

- **Matt Mazur - Step by Step Backprop Example** - Walkthrough numérico completo com valores reais de pesos
  - [mattmazur.com/2015/03/17/a-step-by-step-backpropagation-example](https://mattmazur.com/2015/03/17/a-step-by-step-backpropagation-example)

- **A Not So Random Walk - Backprop with Numbers** - Rede 3-2-2 com formulas derivadas do básico
  - [anotsorandomwalk.com/backpropagation-example-with-numbers-step-by-step](https://anotsorandomwalk.com/backpropagation-example-with-numbers-step-by-step)

- **Prof. Tom Yeh - AI by Hand (Spreadsheet)** - Calcule backprop em células do Excel
  - [byhand.ai/p/backpropagation-spreadsheet](https://byhand.ai/p/backpropagation-spreadsheet)

---

## Ferramentas e Código

- **TensorFlow Playground** - Veja pesos e aprendizado em tempo real
  - [playground.tensorflow.org](https://playground.tensorflow.org)

- **jaymody/backpropagation** - Implementação limpa e mínima focada em entendimento
  - [github.com/jaymody/backpropagation](https://github.com/jaymody/backpropagation)

---

## Otimizadores e Update de Pesos

Backprop calcula os gradientes, mas **como exatamente você atualiza os pesos?**

- **Gradient Descent (vanilla):** `w = w - lr * grad`. Simples, mas sensível ao learning rate.
- **SGD (Stochastic Gradient Descent):** Atualiza com mini-batches ao invés do dataset inteiro. Mais ruidoso, mas muito mais rápido.
- **Adam:** Combina momentum (média móvel dos gradientes) com RMSprop (média móvel dos gradientes ao quadrado). O otimizador padrão para a maioria dos projetos - é o que você vai usar em [[seu-gpt]].

O **learning rate** é o hyperparâmetro mais importante: muito alto e o treino diverge, muito baixo e nunca converge.

---

## Mecânica do Treino

O loop de treinamento completo que conecta tudo:

1. **Forward pass:** dados entram, predições saem
2. **Loss:** compara predições com labels reais
3. **Backward pass:** calcula gradientes via backprop
4. **Update:** aplica otimizador para ajustar pesos
5. **Repita**

Conceitos essenciais:
- **Epoch:** uma passada completa por todo o dataset
- **Batch:** subconjunto dos dados processado de uma vez
- **Monitorar loss:** se o loss de treino desce mas o de validação sobe, você está em overfitting

---

## Insight Chave

**Backprop é "só" a regra da cadeia aplicada recursivamente.** Cada nó no computational graph recebe o gradiente de cima (como sua saída afeta o loss) e passa pra baixo (como seus inputs afetam sua saída). A elegância é que cada nó só precisa de informação local - não precisa "saber" sobre o resto da rede. Isso é o que torna o treinamento de redes profundas computacionalmente viável.

---

## Entregável

**Parte 1 (obrigatória):** Calcule manualmente o backprop para uma rede de 2 inputs, 2 neurônios ocultos, 1 output, usando o walkthrough do Matt Mazur. Faça no papel ou planilha.

**Parte 2:** Seu MLP agora **treina**: Forward → Loss → Backward → Update. Implemente backprop **sem autograd** — escreva as derivadas manualmente para cada camada.

**Alvo:** Faça-o aprender XOR. Após treinamento, deve acertar todas as 4 saídas com loss `< 0.01`.

**Você deve conseguir explicar:** Por que cada nó só precisa de informação local para calcular seu gradiente.

---

## Checklist

- [ ] Assistir Karpathy micrograd completo
- [ ] Assistir 3Blue1Brown backpropagation
- [ ] Ler CS231n backprop notes
- [ ] Ler CS231n optimization notes
- [ ] Fazer exercício do Matt Mazur no papel
- [ ] Implementar backprop no MLP
- [ ] Implementar training loop com SGD
- [ ] Treinar em XOR
- [ ] Verificar que loss diminui

---

## Conexões

> **Fundamento:** Este tópico usa conceitos de [[loss-e-derivadas]]
>
> **Próximo passo:** Aprenda como texto é dividido em tokens em [[tokenizacao]]

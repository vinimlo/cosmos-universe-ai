---
titulo: "MLP e Matrizes"
tags: ["fundamentos", "matemática", "neural", "matrizes", "forward-pass", "broadcasting", "ativações"]
prerequisitos: ["neuronio-e-vetores"]
nivel: "iniciante"
tempoEstimado: 120
autor: "GAEIA"
ultimaAtualizacao: "2026-02-03"
---

# Forward Pass e Matrizes

**Teoria:** Multiplicação de matrizes, broadcasting, transpostas, funções de ativação

**Prática:** Empilhar neurônios em camadas - primeira MLP com forward pass

> Um neurônio é um dot product. Uma camada é uma multiplicação de matrizes. Você sente *na implementação* por que matrizes existem.

---

## Vídeos Fundamentais

- **3Blue1Brown - eps 5-7** - Multiplicação de matrizes como composição de transformações
  - [3blue1brown.com/lessons/matrix-multiplication](https://3blue1brown.com/lessons/matrix-multiplication)

- **Karpathy - micrograd (continuação)** - Construindo operações em grafos computacionais
  - [github.com/karpathy/micrograd](https://github.com/karpathy/micrograd)

---

## Leituras e Tutoriais

- **Jake VanderPlas - Python Data Science Handbook (Broadcasting)** - As 3 regras de broadcasting com analogia de "stretching"
  - [jakevdp.github.io/PythonDataScienceHandbook/02.05](https://jakevdp.github.io/PythonDataScienceHandbook/02.05)

- **NumPy Official - Broadcasting Rules** - Definições autoritativas com tabelas de compatibilidade
  - [numpy.org/doc/stable/user/basics.broadcasting.html](https://numpy.org/doc/stable/user/basics.broadcasting.html)

- **Gregory Gundersen - Matrix Intuition** - Determinantes como escala de área, rank como dimensionalidade
  - [gregorygundersen.com/blog/2018/10/24/matrices](https://gregorygundersen.com/blog/2018/10/24/matrices)

- **ML From Scratch - Neural Network Tutorial** - MLP com MNIST focando forward pass como "dot + activation"
  - [mlfromscratch.com/neural-network-tutorial](https://mlfromscratch.com/neural-network-tutorial)

- **CS231n - Neural Networks Part 1** - Explicação completa de funções de ativação e arquitetura de redes
  - [cs231n.github.io/neural-networks-1](https://cs231n.github.io/neural-networks-1)

---

## Ferramentas Interativas

- **Math is Fun - Transformation Matrices** - Applet interativo com rotação, reflexão, escala
  - [mathsisfun.com/algebra/matrix-transform.html](https://mathsisfun.com/algebra/matrix-transform.html)

---

## Insight Chave

**Por que funções de ativação são essenciais:** Se você empilhar camadas lineares sem ativação, o resultado é... outra transformação linear. Matematicamente, `W2(W1·x) = W3·x` - não importa quantas camadas, a rede só consegue aprender funções lineares. A ativação (sigmoid, ReLU, etc.) quebra essa linearidade e permite que a rede aprenda fronteiras curvas e padrões complexos.

- **Sigmoid:** `1/(1+e^-x)` - você já usou no neurônio. Esmaga em [0,1], mas sofre de gradientes que somem nas extremidades.
- **ReLU:** `max(0, x)` - simples e eficiente, domina redes modernas. Gradiente é 0 ou 1, sem saturação.
- **GELU:** Versão suave do ReLU usada em GPTs (você vai reencontrar em [[seu-gpt]]).

---

## Entregável

MLP com arquitetura `[3, 4, 2]` (3 inputs, camada oculta de 4 neurônios com ReLU, saída de 2 com sigmoid) em NumPy.

**Verificação de shapes:** Imprima o shape de cada ativação intermediária. Se input é `(5, 3)`, após W1 `(3, 4)` você deve ter `(5, 4)`.

**Sem treinar ainda** — só o fluxo pra frente.

**Você deve conseguir explicar:** Por que sem função de ativação, empilhar camadas não ajuda.

---

## Checklist

- [ ] Assistir 3Blue1Brown eps 5-7
- [ ] Ler sobre broadcasting no NumPy
- [ ] Entender multiplicação de matrizes como composição
- [ ] Entender por que ativações são necessárias
- [ ] Implementar MLP com forward pass
- [ ] Testar com dados de exemplo

---

## Conexões

> **Fundamento:** Este tópico usa conceitos de [[neuronio-e-vetores]]
>
> **Próximo passo:** Entenda como medir o erro em [[loss-e-derivadas]]

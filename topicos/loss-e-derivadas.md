---
titulo: "Loss e Derivadas"
tags: ["fundamentos", "matemática", "cálculo", "otimização", "loss", "gradiente"]
prerequisitos: ["mlp-e-matrizes"]
nivel: "intermediario"
tempoEstimado: 120
autor: "GAEIA"
ultimaAtualizacao: "2026-02-03"
---

# Loss, Derivadas e o Por Que do Treinamento

**Teoria:** Derivadas (revisão), conceito de loss function, gradiente como direção

**Prática:** Implementar MSE e cross-entropy, calcular loss do MLP

> "O modelo chutou X, a resposta era Y, quão errado ele está?" Derivadas entram porque você precisa saber *em que direção ajustar* para errar menos.

---

## Vídeos Fundamentais

- **3Blue1Brown - Essence of Calculus** - Derivadas e regra da cadeia com visualizações
  - [youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr](https://youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr)

---

## Leituras e Tutoriais

- **Deep Learning Book (Goodfellow) - Cap. 4** - Diferenciação e álgebra tensorial
  - [deeplearningbook.org](https://deeplearningbook.org)

- **"The Gradient: A Visual Descent"** - Melhor explicação visual: gradiente como generalização n-dimensional da derivada
  - [thelaziestprogrammer.com/sharrington/math-of-machine-learning/the-gradient-a-visual-descent](https://thelaziestprogrammer.com/sharrington/math-of-machine-learning/the-gradient-a-visual-descent)

- **Rohan Varma - Loss Functions** - Demonstra matematicamente por que cross-entropy aprende mais rápido que MSE para classificação
  - [rohanvarma.me/Loss-Functions](https://rohanvarma.me/Loss-Functions)

- **Neural Network in 100 Lines** - Implementa cross-entropy com log-sum-exp trick para estabilidade numérica
  - [papers-100-lines.medium.com/neural-network-from-scratch-in-100-lines-of-python-da89a0ce9b03](https://papers-100-lines.medium.com/neural-network-from-scratch-in-100-lines-of-python-da89a0ce9b03)

---

## Ferramentas Interativas

- **Desmos Calculator** - Plote funções e derivadas com sliders para explorar mudanças de parâmetros
  - [desmos.com/calculator](https://desmos.com/calculator)
  - Pre-built: [Visualizing Derivatives](https://desmos.com/calculator/qhks6uqi7a) | [Intro to Derivatives](https://desmos.com/calculator/5nbrcsw4j2)

---

## Insight Chave

**MSE para regressão, Cross-Entropy para classificação.**

O termo sigma'(z) nos gradientes do MSE causa aprendizado lento quando neurônios saturam. A curva de custo mais ingreme da cross-entropy previne que o modelo fique preso quando predições estão muito erradas.

---

## Entregável

Seu MLP do bloco anterior agora tem dados COM labels (crie pontos 2D sintéticos com classes 0/1) e calcula o loss.

Implemente **MSE** e **Cross-Entropy**. Compare os valores para o mesmo input.

**Gradient check:** Perturbe um peso em `+0.001`, recalcule o loss, e compare `(loss_novo - loss_original) / 0.001` com a derivada analítica. A diferença deve ser `< 1e-5`.

**Você deve conseguir explicar:** "Se eu mexer nesse peso um pouquinho pra cima, o loss sobe ou desce?" — e verificar numericamente.

---

## Checklist

- [ ] Revisar derivadas com 3Blue1Brown
- [ ] Entender gradiente como direção
- [ ] Implementar MSE
- [ ] Implementar Cross-Entropy
- [ ] Calcular loss do MLP
- [ ] Entender quando usar cada loss

---

## Conexões

> **Fundamento:** Este tópico usa conceitos de [[mlp-e-matrizes]]
>
> **Próximo passo:** Aprenda a propagar gradientes em [[backpropagation]]

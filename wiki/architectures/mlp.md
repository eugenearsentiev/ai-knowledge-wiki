---
type: architecture
tags:
  - "architecture"
  - "mlp"
  - "deep-learning"
  - "transformer"
  - "yoshua-bengio"
  - "geoffrey-hinton"
  - "yann-lecun"
---

# Multilayer Perceptron (MLP)

The classic fully-connected neural network. Every neuron in one layer connects to every neuron in the next. The foundational [[deep-learning|deep learning]] building block, and conceptually the simplest neural architecture.

**How it works** — each neuron multiplies inputs by learned weights, sums them, and passes the result through a nonlinear activation function (ReLU, sigmoid, etc.). Learning happens via backpropagation and gradient descent.

**Role today** — MLPs are components inside larger architectures (the feed-forward sub-layers inside [[transformer|Transformers]], classification heads on top of encoders) rather than standalone models. As standalones they're outperformed by specialized architectures for most tasks.

**Historical note** — the single-layer perceptron dates to the 1950s. The key insight that multi-layer networks with backpropagation could learn useful representations was championed by [[yoshua-bengio|Bengio]], [[geoffrey-hinton|Hinton]], and [[yann-lecun|LeCun]] through the 1980s–1990s.

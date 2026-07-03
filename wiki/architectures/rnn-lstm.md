---
type: architecture
tags:
  - "architecture"
  - "rnn-lstm"
  - "nlp"
  - "transformer"
---

# RNNs and LSTMs

Recurrent Neural Networks (RNNs) process sequences one element at a time, maintaining a hidden state that carries information forward. **Long Short-Term Memory (LSTM)** networks added gating mechanisms to handle longer dependencies — a key limitation of vanilla RNNs (the vanishing gradient problem).

**Where they dominated** — [[nlp|NLP]] tasks (language modeling, translation, sentiment analysis) and time-series problems through the mid-2010s. The standard architecture before the [[transformer|Transformer]] largely displaced them.

**Why Transformers won** — Transformers process the whole sequence in parallel (faster training), capture long-range dependencies better through attention, and scale better with data and compute.

**Current relevance** — mostly superseded for language by Transformers, but still used in specific low-latency or embedded applications where sequential processing is a natural fit.

**Historical value** — understanding RNNs/LSTMs explains *why* the Transformer was such a breakthrough.

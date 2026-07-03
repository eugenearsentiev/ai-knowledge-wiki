---
type: concept
tags:
  - "concept"
  - "parameters"
  - "llm"
  - "inference"
  - "rag"
  - "fine-tuning"
  - "quantization"
  - "deep-learning"
  - "pretraining"
---

# Parameters

The learned numerical weights inside a neural network. In [[llm|LLMs]], parameters live across embeddings, attention projections, feed-forward layers, and output heads; training sets them, and [[inference|inference]] runs inputs through them.

**Why they matter** — parameter count is a rough shorthand for model size and capacity. Larger models often handle nuance, reasoning, and broad knowledge better, but they cost more to serve and are slower or harder to run locally.

**Not the whole story** — data quality, architecture, training recipe, alignment, context length, and task fit can matter as much as raw size. A smaller model can beat a larger one on a focused workflow.

**Product lens** — choose models by evals on the real task, not parameter count alone. Pair smaller models with routing, [[rag|RAG]], [[fine-tuning|fine-tuning]], or [[quantization|quantization]] when cost and latency matter.

**Links** — [[llm|LLM]], [[deep-learning|Deep learning]], [[pretraining|Pretraining]], [[quantization|Quantization]].

---
type: architecture
tags:
  - "architecture"
  - "transformer"
  - "attention-is-all-you-need"
  - "llm"
  - "multimodal-ai"
  - "embeddings"
  - "rnn-lstm"
  - "bert"
  - "gpt"
  - "inference"
  - "context-window"
  - "pretraining"
  - "fine-tuning"
  - "claude"
  - "gemini"
  - "llama"
  - "diffusion-models"
---

# Transformer

Introduced in the 2017 paper **[[attention-is-all-you-need|"Attention Is All You Need"]]** (Google), the Transformer is the single most important architecture to understand in modern AI. It is the foundation of [[llm|LLMs]] and has expanded into vision, audio, and [[multimodal-ai|multimodal]] systems.

**Core idea** — **self-attention** weighs the relevance of every position in the input against every other position, all at once. This creates contextual [[embeddings|embeddings]] and enables training on much larger datasets than sequential [[rnn-lstm|RNNs]].

**Variants** — encoder-only ([[bert|BERT]], for understanding/embeddings), decoder-only ([[gpt|GPT]] family, for generation), encoder-decoder (translation, T5). Most modern LLMs are decoder-only.

**Runtime role** — during [[inference|inference]], tokens inside the [[context-window|context window]] pass through stacked Transformer layers; the model then predicts and samples the next token.

**Why it won** — scales remarkably well with compute and data; generalizes across domains; enables transfer learning via [[pretraining|pretraining]] → [[fine-tuning|fine-tuning]].

**Virtually all modern large models use it** — [[gpt|GPT]], [[claude|Claude]], [[gemini|Gemini]], [[llama|Llama]], [[bert|BERT]], Vision Transformers (ViT), and [[diffusion-models|diffusion model]] backbones.

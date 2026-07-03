---
type: concept
tags:
  - "concept"
  - "llm"
  - "tokenization"
  - "pretraining"
  - "fine-tuning"
  - "rlhf"
  - "gpt"
  - "openai"
  - "claude"
  - "anthropic"
  - "gemini"
  - "google-deepmind"
  - "llama"
  - "meta-ai"
  - "deepseek"
  - "prompting"
  - "rag"
  - "lora"
  - "quantization"
  - "agents-tool-use"
  - "inference"
  - "context-window"
  - "parameters"
  - "sampling"
  - "hallucination"
  - "model-evals"
  - "ollama"
  - "lm-studio"
  - "transformer"
  - "deep-learning"
  - "generative-ai"
---

# Large Language Models (LLMs)

Transformer-based neural networks trained on vast text corpora to predict the next [[tokenization|token]]. That simple objective, scaled to enormous models and datasets, yields systems that write, summarize, translate, reason, and generate code.

**Training pipeline** — **[[pretraining|Pretraining]]** on a broad corpus builds general capability; **[[fine-tuning|fine-tuning]]** and alignment steps (especially **[[rlhf|RLHF]]**) make the model safe and helpful for specific uses.

**Key models** — [[gpt|GPT]] ([[openai|OpenAI]]), [[claude|Claude]] ([[anthropic|Anthropic]]), [[gemini|Gemini]] ([[google-deepmind|Google DeepMind]]), [[llama|Llama]] ([[meta-ai|Meta AI]]), [[deepseek|DeepSeek]].

**Key techniques** — [[prompting|Prompting]] (most accessible lever), [[rag|RAG]] (external knowledge), [[fine-tuning|fine-tuning]], [[lora|LoRA]] (parameter-efficient adaptation), [[quantization|quantization]] (run on smaller hardware), [[agents-tool-use|agents and tool use]].

**Runtime basics** — an LLM call is [[inference|inference]]: input text is tokenized, placed in a [[context-window|context window]], processed by fixed [[parameters|parameters]], and decoded with [[sampling|sampling]] controls such as temperature.

**Product readiness** — because outputs are open-ended and nondeterministic, teams use [[model-evals|model evals]] to test quality, safety, cost, and regressions before switching prompts or model versions.

**Reliability watchout** — [[hallucination]] is the core product failure mode: fluent answers can be unsupported, fabricated, or wrong even when the model sounds confident.

**Closed vs. open-weight** — closed/proprietary (API access only) vs. open-weight (downloadable, runnable locally via [[ollama|Ollama]] or [[lm-studio|LM Studio]]).

**Parent architecture** — [[transformer|Transformer]] → [[deep-learning|Deep Learning]] → [[generative-ai|Generative AI]].

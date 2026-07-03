---
type: concept
tags:
  - "concept"
  - "inference"
  - "parameters"
  - "tokenization"
  - "transformer"
  - "prompting"
  - "context-window"
  - "rag"
  - "sampling"
  - "llm"
  - "quantization"
---

# Inference

The runtime event where a trained model receives a prompt and generates output. During [[inference|inference]], the model's [[parameters|parameters]] are fixed; it is not learning from the prompt unless a separate training or memory system records something.

**LLM loop** — text is [[tokenization|tokenized]], converted into vectors, processed through [[transformer|Transformer]] layers, then decoded one token at a time until the response is complete.

**Two phases** — prefill reads the input context; decoding produces the answer token by token. Long prompts increase prefill cost and latency, while long answers increase decoding cost and latency.

**Product lens** — inference is where [[prompting|prompts]], [[context-window|context windows]], [[rag|RAG]], [[sampling|sampling settings]], tool results, and model choice become user-visible behavior.

**Links** — [[llm|LLM]], [[transformer|Transformer]], [[tokenization|Tokenization]], [[sampling|Sampling]], [[quantization|Quantization]].

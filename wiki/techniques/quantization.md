---
type: technique
tags:
  - "technique"
  - "quantization"
  - "llm"
  - "ollama"
  - "lora"
  - "llama"
---

# Quantization

Reducing the numerical precision of model weights — and sometimes activations — to shrink model size and speed up inference. A model trained in 32-bit or 16-bit floating point can be quantized to 8-bit integers (INT8) or 4-bit, drastically reducing memory footprint.

**Why it matters** — frontier [[llm|LLMs]] have billions of parameters; in full precision they require expensive GPUs. Quantization makes them runnable on consumer hardware: a 70B-parameter model at 4-bit can fit on a high-end consumer GPU.

**Tradeoff** — some accuracy loss, typically small at 8-bit and acceptable at 4-bit with modern techniques. More aggressive quantization degrades quality more.

**Common formats** — GGUF (CPU/GPU, used by llama.cpp / [[ollama|Ollama]]), GPTQ, AWQ (GPU-optimized).

**Related** — **QLoRA** combines quantization with [[lora|LoRA]] for memory-efficient fine-tuning.

**Links** — [[llm|LLM]], [[lora|LoRA]], [[ollama|Ollama]], [[llama|Llama]].

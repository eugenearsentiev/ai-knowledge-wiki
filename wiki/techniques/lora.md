---
type: technique
tags:
  - "technique"
  - "lora"
  - "fine-tuning"
  - "llm"
  - "llama"
  - "hugging-face"
  - "quantization"
---

# LoRA (Low-Rank Adaptation)

A parameter-efficient [[fine-tuning|fine-tuning]] method. Instead of updating all weights in a large model, LoRA inserts small trainable low-rank matrices alongside the frozen original weights. Only these small matrices are trained; at inference they can be merged back in or applied as a separate adapter.

**Why it matters** — fine-tuning a full [[llm|LLM]] requires substantial GPU memory. LoRA reduces trainable parameters by 10–100× while achieving comparable results, making fine-tuning accessible on consumer hardware.

**Practical use** — the dominant method in the open-source community for creating fine-tuned variants of [[llama|Llama]], Mistral, and other open-weight models. [[hugging-face|Hugging Face]]'s `peft` library is the standard implementation.

**Related methods** — **QLoRA** (LoRA + [[quantization|quantization]] for even lower memory), prefix tuning, adapters.

**Links** — [[fine-tuning|Fine-tuning]], [[llm|LLM]], [[quantization|Quantization]], [[hugging-face|Hugging Face]], [[llama|Llama]].

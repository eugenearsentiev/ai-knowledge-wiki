---
type: technique
tags:
  - "technique"
  - "fine-tuning"
  - "llm"
  - "lora"
  - "rlhf"
  - "rag"
  - "pretraining"
---

# Fine-tuning

Further training a pretrained model on domain-specific or task-specific data. The model starts from its broad pretrained weights and adapts them to a narrower distribution.

**Why** — a general-purpose [[llm|LLM]] may not follow your format, speak your domain's language, or have the right tone. Fine-tuning narrows the model to your use case without training from scratch.

**Full fine-tuning** — update all weights. Expensive; requires substantial GPU and data.

**Parameter-efficient methods** — train only a small fraction of added parameters. [[lora|LoRA]] is the dominant approach: add low-rank weight matrices, train only those. Enables fine-tuning on consumer hardware.

**[[rlhf|RLHF]]** — a fine-tuning approach using human preference data; how major labs turn base models into helpful assistants.

**vs. [[rag|RAG]]** — fine-tuning bakes knowledge into weights; RAG adds it at inference time. Complementary: fine-tune for behavior/style, use RAG for up-to-date knowledge.

**Links** — [[llm|LLM]], [[lora|LoRA]], [[rlhf|RLHF]], [[rag|RAG]], [[pretraining|Pretraining]].

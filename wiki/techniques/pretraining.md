---
type: technique
tags:
  - "technique"
  - "pretraining"
  - "llm"
  - "gpt"
  - "bert"
  - "fine-tuning"
  - "rlhf"
  - "transformer"
---

# Pretraining

The first and largest training phase for modern deep learning models. A model is trained on a massive, broad dataset to learn general representations — language understanding for [[llm|LLMs]], image features for vision models.

**For LLMs** — next-token prediction on trillions of tokens (autoregressive / decoder-only, like [[gpt|GPT]]) or masked language modeling (encoder models like [[bert|BERT]]). Scale of pretraining data and model size is what gives frontier models their breadth.

**Why it matters** — pretraining creates a strong general prior; [[fine-tuning|fine-tuning]] and [[rlhf|RLHF]] then adapt it cheaply. Without large-scale pretraining, fine-tuning on small domain datasets produces weak models.

**Transfer learning** — the pretrain → fine-tune pattern is called transfer learning. One of the most powerful practical ideas in modern ML: train once on broad data, adapt many times to specific tasks.

**Enabled by** — the [[transformer|Transformer]]'s parallelism made training on this scale computationally feasible.

**Links** — [[llm|LLM]], [[fine-tuning|Fine-tuning]], [[rlhf|RLHF]], [[transformer|Transformer]], [[bert|BERT]], [[gpt|GPT]].

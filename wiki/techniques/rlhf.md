---
type: technique
tags:
  - "technique"
  - "rlhf"
  - "reinforcement-learning"
  - "pretraining"
  - "openai"
  - "chatgpt"
  - "anthropic"
  - "fine-tuning"
  - "llm"
  - "model-evals"
---

# RLHF (Reinforcement Learning from Human Feedback)

The training technique that turns a pretrained language model into a helpful assistant. Human raters compare model outputs; those preferences train a **reward model**; the reward model guides [[reinforcement-learning|reinforcement learning]] (typically PPO) to update the LLM.

**Why it works** — raw [[pretraining|pretraining]] produces a model that predicts text well but doesn't reliably follow instructions. RLHF shapes it toward what humans find helpful, harmless, and honest.

**Evaluation connection** — the same pairwise human preference pattern also appears in [[model-evals|model evals]], where raters compare outputs for helpfulness, tone, accuracy, and fit to task.

**Variants** — **RLAIF** (RL from AI Feedback — use another model instead of humans, cheaper at scale), **DPO** (Direct Preference Optimization — a simpler alternative that skips the separate reward model).

**Who uses it** — [[openai|OpenAI]] (InstructGPT, [[chatgpt|ChatGPT]]), [[anthropic|Anthropic]] (Constitutional AI extends RLHF with a written set of principles), virtually all major labs.

**Links** — [[fine-tuning|Fine-tuning]], [[llm|LLM]], [[reinforcement-learning|RL]], [[pretraining|Pretraining]], [[model-evals]].

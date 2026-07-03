---
type: model
tags:
  - "model"
  - "claude"
  - "anthropic"
  - "rlhf"
  - "transformer"
  - "llm"
---

# Claude

[[anthropic|Anthropic]]'s flagship model family, designed with a strong safety focus. Uses **Constitutional AI** — a variant of [[rlhf|RLHF]] that uses a written set of principles rather than purely human ratings, reducing dependence on human labeling at scale.

**Versions** — Claude 1 → Claude 2 → Claude 3 family (Haiku / Sonnet / Opus tiers for cost-capability tradeoffs) → Claude 4 family. The tiered naming reflects different cost/performance points.

**Capabilities** — long context windows (100K+ tokens), strong reasoning, coding, and analysis. Multimodal (image input). Claude 3.5 Sonnet set notable benchmarks in coding tasks.

**Alignment approach** — Anthropic frames its goals as "helpful, harmless, honest" (HHH). Constitutional AI lets a model critique and revise its own outputs against a set of principles.

**Model vs. product** — Claude is the model/API; Claude.ai is the consumer interface; Claude Code is the developer CLI.

**Links** — [[anthropic|Anthropic]], [[transformer|Transformer]], [[rlhf|RLHF]], [[llm|LLM]].

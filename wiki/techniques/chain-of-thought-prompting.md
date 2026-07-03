---
type: technique
tags:
  - "technique"
  - "chain-of-thought-prompting"
  - "rag"
  - "prompting"
  - "llm"
  - "agents-tool-use"
---

# Chain-of-Thought Prompting

Prompting pattern that asks a model to reason through a problem before giving an answer. In practice, product prompts often ask for a short rationale, assumptions, or key tradeoffs rather than a long reasoning trace.

**Use cases** — prioritization, planning, debugging, comparison, math-like problems, and multi-step decisions. Example framing: "Compare these roadmap options by customer impact, engineering effort, and strategic fit; then recommend one with a brief rationale."

**Why it helps** — it slows the task down and encourages the model to organize intermediate considerations instead of jumping to a shallow answer.

**Caution** — reasoning text is not proof of correctness. For factual work, pair this with [[rag|retrieval]], citations, or tool checks.

**Links** — [[prompting]], [[llm]], [[rag]], [[agents-tool-use]].

---
type: technique
tags:
  - "technique"
  - "few-shot-prompting"
  - "llm"
  - "context-window"
  - "prompt-templates"
  - "prompting"
  - "zero-shot-prompting"
  - "structured-output-prompting"
---

# Few-Shot Prompting

Give an [[llm|LLM]] a few examples of the desired input-output pattern before asking it to complete the real task.

**Why it matters** — examples teach the model the local convention: labels, tone, formatting, or decision boundaries. For support tickets, examples can show that "charged twice" maps to Billing while "dashboard crashes" maps to Bug.

**Common uses** — classification, style matching, extraction, consistent formatting, domain-specific triage, and rubrics where the model needs to imitate a pattern.

**Tradeoff** — examples consume [[context-window|context]] and can bias the model. Keep them representative and non-conflicting. If the task becomes repeatable across many calls, examples often become part of a [[prompt-templates|prompt template]] or evaluation set.

**Links** — [[prompting]], [[zero-shot-prompting]], [[context-window]], [[structured-output-prompting]].

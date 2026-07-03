---
type: technique
tags:
  - "technique"
  - "zero-shot-prompting"
  - "llm"
  - "prompting"
  - "few-shot-prompting"
  - "prompt-templates"
  - "structured-output-prompting"
---

# Zero-Shot Prompting

Ask an [[llm|LLM]] to perform a task directly without examples. The model relies on its pretrained instruction-following ability plus the wording of the prompt.

**Common uses** — summarization, rewriting, brainstorming, simple classification, simple extraction, and first-pass analysis. A zero-shot prompt can be as direct as: "Summarize this article in five bullet points for a non-technical audience."

**Strength** — fast to write and often good enough for familiar tasks. It is the default starting point for [[prompting|prompt engineering]].

**Limit** — if the task requires a specific style, label scheme, or judgment standard, the model may infer the wrong pattern. Move to [[few-shot-prompting|few-shot prompting]] or [[prompt-templates|prompt templates]] when consistency matters.

**Links** — [[prompting]], [[llm]], [[few-shot-prompting]], [[structured-output-prompting]].

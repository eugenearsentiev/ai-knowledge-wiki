---
type: technique
tags:
  - "technique"
  - "prompt-templates"
  - "prompting"
  - "rag"
  - "context-window"
  - "structured-output-prompting"
  - "few-shot-prompting"
---

# Prompt Templates

Reusable prompt patterns that standardize repeated [[prompting|LLM]] tasks. A template usually contains slots for the task, source text, audience, constraints, examples, and output format.

**Typical components** — role, task, context, source material, constraints, quality bar, and output format. Delimiters such as triple backticks, XML-style tags, or section headings separate instructions from source material.

**Why they matter** — templates make outputs more consistent across users, documents, and repeated workflows. They are common in support triage, product review, research synthesis, extraction, and [[rag|retrieval]] prompts.

**Good template behavior** — say what to do when information is missing, avoid conflicting instructions, and keep irrelevant context out of the [[context-window|context window]].

**Links** — [[prompting]], [[structured-output-prompting]], [[few-shot-prompting]], [[rag]], [[context-window]].

---
type: technique
tags:
  - "technique"
  - "guardrails"
  - "hallucination"
  - "llm"
  - "rag"
  - "agents-tool-use"
  - "faithfulness"
  - "groundedness"
---

# Guardrails

Guardrails are controls around an [[llm|LLM]] application that constrain inputs, retrieval, tool use, dialogue flow, or outputs. They do not make models truthful by themselves, but they help catch and contain [[hallucination]] and other product risks before users see or act on bad output.

Common rails include input filters, prompt-injection checks, retrieval filters, topic boundaries, structured-output validation, citation requirements, sensitive-data masking, and output checks. In [[rag|RAG]], a faithfulness gate can compare generated claims against retrieved documents and return a fallback when support is weak.

**Real-time gates** score an answer before it reaches the user. If [[faithfulness]] or [[groundedness]] is below a chosen threshold, the system can block the answer and say it cannot find confident support in the knowledge base.

Guardrails are most useful as part of a system: [[prompting]] shapes the answer, retrieval grounds it, [[model-evals]] measure regressions, and human review handles high-stakes exceptions. Overreliance is risky: weak guardrails can create a false sense of safety, and strict guardrails can block useful answers.

**Links** — [[hallucination]], [[faithfulness]], [[groundedness]], [[rag]], [[prompting]], [[agents-tool-use]], [[model-evals]].

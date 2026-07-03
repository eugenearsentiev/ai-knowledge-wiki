---
type: technique
tags:
  - "technique"
  - "llm-as-judge"
  - "model-evals"
  - "llm"
  - "structured-output-prompting"
  - "hallucination"
  - "faithfulness"
  - "rag-evaluation"
---

# LLM-as-Judge

LLM-as-judge is an evaluation technique where a strong [[llm|LLM]] grades another model's output against a rubric, reference answer, or pairwise preference prompt. It is a practical way to automate parts of [[model-evals|model evals]] when human review is too slow or expensive.

Common uses: regression tests for prompt changes, grading open-ended answers, comparing model versions, checking formatting, and triaging large evaluation sets before human review.

For [[hallucination]] checks, a judge can break an answer into claims and compare them with a reference answer or retrieved context. This is especially useful for [[faithfulness]] scoring in [[rag|RAG]] systems and broader [[rag-evaluation|RAG evaluation]].

The hard part is trust. A judge model can be biased, overly harsh, too lenient, or sensitive to wording. Teams validate it by measuring agreement with human annotators and by using consistent rubrics, often with [[structured-output-prompting|structured outputs]].

Some judge setups optimize for human-like nuance; others optimize for reproducible consistency. The better choice depends on whether the product needs subjective quality assessment or strict compliance checks.

**Links** — [[model-evals]], [[ai-benchmarks]], [[llm]], [[structured-output-prompting]], [[hallucination]], [[faithfulness]], [[rag-evaluation]].

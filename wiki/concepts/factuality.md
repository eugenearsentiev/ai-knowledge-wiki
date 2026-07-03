---
type: concept
tags:
  - "concept"
  - "factuality"
  - "hallucination"
  - "llm"
  - "model-evals"
---

# Factuality

Factuality is whether an AI answer's claims are true with respect to the outside world. It is one lens for detecting [[hallucination]] in [[llm|LLM]] applications.

A factuality failure can be **intrinsic**, where the model contradicts known ground truth, or **extrinsic**, where it invents extra claims that sound plausible but lack evidence. Fabricated citations, wrong dates, misattributed quotes, and invented product capabilities are common product-facing examples.

Factuality is hard because real-world truth may be ambiguous, time-sensitive, private, or missing from the model's training data. For fast-moving topics, teams usually pair the model with [[rag|RAG]], tools, or human review instead of relying on model memory.

In [[model-evals]], factuality checks work best when test cases include reference answers, source documents, or explicit rubrics. [[llm-as-judge|LLM-as-judge]] can triage large sets, but should be calibrated against human review for high-stakes domains.

**Links** — [[hallucination]], [[faithfulness]], [[model-evals]], [[rag]], [[llm-as-judge]].


---
type: technique
tags:
  - "technique"
  - "rag-evaluation"
  - "rag"
  - "model-evals"
  - "hallucination"
  - "faithfulness"
  - "groundedness"
---

# RAG Evaluation

RAG evaluation checks whether a [[rag|RAG]] system retrieved the right evidence and generated an answer supported by that evidence. It is more diagnostic than a single accuracy score because RAG failures can happen in indexing, retrieval, prompting, generation, citation, or post-processing.

Core lenses: **[[context-recall]]** asks whether retrieval found the needed facts; **answer relevance** asks whether the response addresses the question; **[[faithfulness]]** and **[[groundedness]]** ask whether generated claims are supported by retrieved context.

Frameworks such as RAGAs use [[llm-as-judge|LLM-as-judge]] style checks to break answers into claims and compare them with retrieved chunks. Lightweight classifiers can also cross-check claims against context.

The practical goal is error isolation: if recall fails, tune retrieval; if faithfulness fails, improve prompting, generation, citation checks, or [[guardrails]].

**Links** - [[rag]], [[model-evals]], [[hallucination]], [[context-recall]], [[faithfulness]], [[groundedness]].


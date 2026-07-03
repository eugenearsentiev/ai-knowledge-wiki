---
type: concept
tags:
  - "concept"
  - "groundedness"
  - "hallucination"
  - "rag"
  - "faithfulness"
  - "model-evals"
---

# Groundedness

Groundedness is whether an AI answer is anchored in supplied evidence: retrieved documents, tool outputs, database records, or other authoritative context. In [[rag|RAG]], it is the product promise that answers are based on the knowledge base rather than the model's internal memory.

It overlaps with [[faithfulness]]. A grounded answer should not add claims that the retrieved context does not support; it should also avoid citation mismatch, where a source is cited but does not actually contain the claim.

Groundedness failures often come from retrieval problems rather than generation alone: missing documents, outdated chunks, noisy results, poor chunking, or conflicting context. The model may then fill gaps with plausible but unsupported text.

Practical checks include source-backed answer review, [[llm-as-judge|LLM-as-judge]] claim verification, context recall, attribution checks, and production [[model-evals]] that track trend lines over time.

**Links** - [[hallucination]], [[faithfulness]], [[rag]], [[rag-evaluation]], [[model-evals]].


---
type: concept
tags:
  - "concept"
  - "context-recall"
  - "rag"
  - "model-evals"
  - "hallucination"
---

# Context Recall

Context recall is a [[rag|RAG]] evaluation lens: did retrieval bring back the information needed to answer the user's question?

It helps separate retrieval failures from generation failures. If context recall is low, the model may be doing the best it can with missing evidence; the fix is usually indexing, chunking, query rewriting, metadata filtering, or retrieval tuning. If context recall is high but the answer is unsupported, the problem is more likely [[faithfulness]], prompting, or generation behavior.

Context recall matters because RAG hallucinations often begin before the model writes anything. Arbitrary chunk boundaries can split a rule, definition, or exception across chunks, so the model sees only half the needed facts and guesses the rest.

In practice, context recall is tracked alongside [[groundedness]], answer relevance, citation checks, and [[model-evals]] over repeated test sets.

**Links** - [[rag]], [[hallucination]], [[faithfulness]], [[groundedness]], [[rag-evaluation]].


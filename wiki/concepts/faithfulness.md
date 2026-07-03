---
type: concept
tags:
  - "concept"
  - "faithfulness"
  - "hallucination"
  - "rag"
  - "model-evals"
  - "llm-as-judge"
  - "groundedness"
---

# Faithfulness

Faithfulness is whether an AI answer is supported by the context it was supposed to use: the prompt, retrieved documents, tool outputs, or conversation state. It is especially important in [[rag|RAG]], where the product promise is grounded answers, not model memory.

A faithful answer may still be incomplete, but it should not add claims the provided context does not support. Common failures include changing a document's meaning, [[citation-mismatch|citing a source that does not contain the claim]], ignoring a constraint, or producing reasoning that contradicts earlier steps.

Faithfulness is related to [[factuality]] but not identical. A claim can be true in the world yet unfaithful to the supplied source; a claim can also be faithful to a flawed source while factually wrong.

Evaluation often breaks an answer into atomic claims, checks each against the retrieved context, and tracks trend lines in [[model-evals]]. [[rag-evaluation|RAG evaluation]] pairs faithfulness with [[context-recall]] to isolate retrieval failures from generation failures.

**Links** — [[hallucination]], [[factuality]], [[groundedness]], [[rag]], [[model-evals]], [[llm-as-judge]].

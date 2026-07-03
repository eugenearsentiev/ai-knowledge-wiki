---
type: concept
tags:
  - "concept"
  - "citation-mismatch"
  - "hallucination"
  - "rag"
  - "groundedness"
---

# Citation Mismatch

Citation mismatch is a [[rag|RAG]] failure where an answer cites a document, passage, or reference that does not actually support the claim being made.

It is especially dangerous because it gives unsupported output the appearance of evidence. A user may trust the answer because it has a citation, even though the cited source is irrelevant, incomplete, outdated, or only loosely related.

Citation mismatch is a form of [[hallucination]] when the model fabricates support or attaches real sources to invented claims. It can happen even when retrieval finds useful documents, because the generation layer may overstate, blend, or misattribute information across chunks.

Practical defenses include claim-level source checks, quoted evidence snippets, stricter answer templates, [[groundedness]] scoring, human review for high-stakes claims, and [[guardrails]] that block answers when support is weak.

**Links** - [[hallucination]], [[rag]], [[faithfulness]], [[groundedness]], [[guardrails]].


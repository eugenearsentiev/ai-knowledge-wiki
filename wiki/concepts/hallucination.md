---
type: concept
tags:
  - "concept"
  - "hallucination"
  - "llm"
  - "factuality"
  - "faithfulness"
  - "groundedness"
  - "rag"
  - "model-evals"
---

# Hallucination

Hallucination is a practical failure mode where an [[llm|LLM]] produces fluent, plausible output that is factually wrong, fabricated, or unsupported by the evidence available to the system.

Two useful lenses: **[[factuality]]** asks whether a claim is true in the world; **[[faithfulness]]** asks whether it is supported by the prompt, retrieved documents, or tool results. A model can sound confident while inventing citations, adding unsupported details, or guessing when the answer is not in context.

Why it happens: LLMs are trained to predict likely text, not to guarantee truth. [[rlhf|RLHF]] and assistant tuning can also create pressure to be helpful rather than to say "I don't know." In [[rag|RAG]], hallucination often shifts from model memory to retrieval quality: bad chunking, missing context, irrelevant documents, context conflicts, or [[citation-mismatch|citation mismatch]] leave the model to fill gaps.

Mitigation is containment: better [[prompting]], [[rag|RAG]], citations, [[guardrails]], [[llm-as-judge|LLM-as-judge]] checks, [[rag-evaluation|RAG evaluation]], human review, and production [[model-evals]].

---
type: concept
tags:
  - "concept"
  - "context-window"
  - "llm"
  - "inference"
  - "tokenization"
  - "rag"
  - "prompting"
  - "open-brain"
---

# Context Window

The temporary working memory available to an [[llm|LLM]] during a single [[inference|inference]] call. It contains system instructions, conversation history, retrieved documents, tool outputs, and the current user message, all measured in [[tokenization|tokens]].

**Why it matters** — the model can only use information present in the current context. If an application needs memory, private data, or fresh facts, it must inject them through [[rag|RAG]], summaries, stored preferences, or tool results.

**Long context tradeoff** — larger windows allow document-scale work, but they raise latency and cost. They also do not guarantee perfect attention: important material buried in the middle of very long prompts may be underused.

**Design heuristic** — keep critical instructions and evidence easy to find; avoid carrying unnecessary history; measure token counts before deploying high-volume workflows.

**Links** — [[llm|LLM]], [[tokenization|Tokenization]], [[rag|RAG]], [[prompting|Prompting]], [[open-brain|Open Brain]].

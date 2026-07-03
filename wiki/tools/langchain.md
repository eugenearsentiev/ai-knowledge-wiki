---
type: tool
tags:
  - "tool"
  - "langchain"
  - "llm"
  - "agents-tool-use"
  - "rag"
  - "prompting"
---

# LangChain

A Python (and JavaScript) framework for building applications on top of [[llm|LLMs]]. Provides abstractions for chaining LLM calls, managing prompts, integrating tools, and building [[agents-tool-use|agentic]] workflows.

**Core abstractions** — chains (sequences of LLM calls), agents (LLMs that choose and use tools in a loop), memory, document loaders, text splitters, and vector store integrations (for [[rag|RAG]]).

**LangGraph** — an extension for building stateful multi-agent workflows as directed graphs; the more robust approach for complex long-running agents.

**Ecosystem** — LangSmith (observability and tracing for LLM apps), LangServe (deploy chains as APIs).

**Reception** — the most-starred LLM framework (early mover advantage), but also criticized for over-abstraction that obscures what's actually happening. Many teams simplify away from LangChain once they understand the primitives well enough to build their own.

**Links** — [[llm|LLM]], [[rag|RAG]], [[agents-tool-use|Agents]], [[prompting|Prompting]].

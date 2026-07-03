---
type: technique
tags:
  - "technique"
  - "agents-tool-use"
  - "langchain"
  - "open-brain"
  - "spec-driven-development"
  - "github-spec-kit"
  - "kiro"
  - "llm"
  - "prompting"
  - "rag"
  - "hallucination"
  - "guardrails"
---

# Agents and Tool Use

An **LLM agent** goes beyond single-turn question answering: it can call external tools (web search, code execution, APIs, databases), take multi-step actions, and orchestrate workflows. The LLM acts as the reasoning engine; tools extend what it can do.

**Core pattern** — a reasoning loop: observe → think → act → observe the result → continue. ReAct (Reason + Act) is a foundational prompting pattern for this loop.

**Common tools** — web search, code interpreter, database queries, file I/O, API calls, memory systems, and other models. Multi-agent frameworks have LLMs orchestrate other LLMs.

**Frameworks** — [[langchain|LangChain]] / LangGraph, AutoGen, and similar wrap the agentic loop and manage tool integration. [[open-brain|Open Brain]] provides persistent memory that agents can write to and recall from. [[spec-driven-development|Spec-driven development]] tools such as [[github-spec-kit|GitHub Spec Kit]] and [[kiro|Kiro]] add structured specs, plans, and tasks around agent execution.

**Emerging importance** — agents are becoming the primary use case for frontier [[llm|LLMs]] in production applications.

**Reliability watchout** — agents can amplify [[hallucination]] when they invent tool results, assume state that was not observed, or act before verifying. [[guardrails|Guardrails]] and tool-result checks matter more as actions become consequential.

**Links** — [[llm|LLM]], [[prompting|Prompting]], [[rag|RAG]], [[langchain|LangChain]], [[open-brain|Open Brain]], [[spec-driven-development]], [[hallucination]], [[guardrails]].

---
type: tool
tags:
  - "tool"
  - "open-brain"
  - "rag"
  - "agents-tool-use"
  - "llm"
---

# Open Brain

An open-source, self-hosted **persistent memory layer** for AI tools. Captures discrete "thoughts" (facts, decisions, preferences, notes), embeds them for semantic search, and lets any MCP-compatible client (Claude, Cursor, Copilot, ChatGPT, etc.) recall them by meaning across sessions and tools.

**Architecture** — [[rag|RAG]] under the hood: embed → store in PostgreSQL + pgvector → semantic vector search → inject into LLM context. Framed as a memory layer rather than a document-retrieval pipeline; the atomic unit is a **thought**, not a document chunk.

**MCP-native** — exposes 7 tools via the Model Context Protocol: `capture_thought`, `search_thoughts`, `list_thoughts`, `update_thought`, `delete_thought`, `capture_thoughts`, `thought_stats`. Also a REST API on port 8000.

**vs. traditional [[rag|RAG]]** — RAG is for external authoritative corpora; Open Brain is for evolving personal/agent context (decisions, preferences, project history). They're complementary.

**Closest peer** — Mem0 (cloud-hosted, lower-friction alternative).

*Source: `open-brain-reference.md`*

**Links** — [[rag|RAG]], [[agents-tool-use|Agents]], [[llm|LLM]].

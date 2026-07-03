# Open Brain — Reference Summary

A quick-reference guide to understand what Open Brain is, how it works, and when to reach for it.

---

## TL;DR

Open Brain is an **open-source, self-hosted, MCP-native persistent memory layer for AI tools**. It captures notes, decisions, preferences, and context as discrete "thoughts," embeds them for semantic search, and lets any AI client (Claude, Cursor, Copilot, ChatGPT, etc.) recall them by meaning across sessions and tools. Your data stays on your own infrastructure.

Under the hood it is a RAG system (embed → store in pgvector → semantic search → feed to an LLM), but it is *framed and packaged as a memory layer* rather than a document-retrieval pipeline.

- **Repo:** github.com/srnichols/OpenBrain — **Docs:** srnichols.github.io/OpenBrain
- **License:** MIT — **Origin:** architecture by Nate B Jones, extended/self-hosted by Scott Nichols

---

## First: which "Open Brain"?

The name is overloaded. If you encounter "Open Brain," confirm which one is meant:

| Name | What it is |
|---|---|
| **Open Brain** (this doc) | Persistent semantic memory layer for AI tools (MCP, pgvector) |
| **Open Brain Institute** | Neuroscience non-profit; cloud "Virtual Labs" for building/simulating digital brain models |
| **Open Brain AI (OBAI)** | NLP platform for clinicians — transcription, translation, language assessment |
| **NeuroTrALE** | MIT open-source tool for automated axon tracing and brain-mapping |

The rest of this document covers only the first one.

---

## Mental model

Think of it as **"long-term memory for your AI assistants."** Today each chat starts cold and forgets everything. Open Brain gives your tools a shared, searchable memory that persists between sessions and is available from *any* MCP-compatible client — so context isn't trapped inside one app's history.

The atomic unit is a **thought**: a discrete fact, decision, preference, or note — not a document. This is the key distinction from document-RAG, which deals in chunks of source files.

---

## Architecture

One server sits between your AI clients and a single Postgres database.

```
AI clients (Claude, Cursor, Copilot, ChatGPT, ...)
        │  MCP (port 8080) or REST (port 8000)
        ▼
   Open Brain server  ──►  Embedder (Ollama / OpenRouter / Azure OpenAI)
   capture·embed·       ──►  Metadata LLM (extracts type, topics, people)
   classify·search
        │
        ▼
   PostgreSQL + pgvector
   (one "thoughts" table: vector + JSONB metadata)
```

Design principle: keep the moving parts minimal. Embeddings and relational metadata live in the **same Postgres instance** (via pgvector) — no separate vector database to synchronize.

### Data flow

1. **Capture** — an AI tool calls `capture_thought` via MCP (also possible: REST API, Slack webhook, bulk import from Notion/Obsidian).
2. **Embed & tag** — the thought is embedded into a 768-dimension vector, and a small LLM extracts metadata (type, topics, people, action items) in parallel, typically under ~3 seconds.
3. **Store** — saved to a single `thoughts` table; HNSW index for fast vector search, GIN index for metadata filtering.
4. **Recall** — any client calls `search_thoughts` to find memories by meaning, even when the wording differs.

### What a stored "thought" contains

A single row holds the raw content, extracted fields (type, topics, people, created_by, timestamp), a JSONB metadata blob, and a 768-dim embedding vector beside it. This supports three retrieval modes at once: semantic (vector), structured filtering (columns/GIN), and provenance lookup (JSONB). The optional **Hallmark provenance** envelope carries `contentHash`, `codeHash`, phase, and tool — letting you trace a memory back to its exact source.

---

## The tool API (7 MCP tools)

Every operation is exposed as both an MCP tool and a REST endpoint.

| Tool | Purpose |
|---|---|
| `search_thoughts` | Semantic vector search — find by meaning |
| `capture_thought` | Store one thought (auto-embed + classify) |
| `capture_thoughts` | Batch-store many thoughts at once |
| `list_thoughts` | Filter by type, topic, person, or date |
| `update_thought` | Edit content and re-embed |
| `delete_thought` | Remove a thought by ID |
| `thought_stats` | Aggregate stats, top topics, top people |

Clients can probe `GET /health` for a `capabilities[]` array (v0.7.0+).

---

## Key features / differentiators

- **Semantic search** — meaning-based recall on top of Postgres, results in milliseconds.
- **Auto metadata** — every thought classified by type, topics, people, dates; no manual tagging.
- **MCP-native** — one backend works across 9+ AI clients (Copilot, Claude Desktop, Claude Code, Cursor, ChatGPT, Gemini, Grok, Windsurf, any MCP client).
- **Private & self-hosted** — runs on your own hardware; memories never leave your infrastructure.
- **Single Postgres + pgvector** — no separate vector store to operate or sync.
- **Provenance / traceability** — signed source-hash envelopes trace memories to their origin.
- **Offline-safe** — when the store is unreachable, writes queue locally and drain later (no thought lost).

---

## Main use cases

- **Cross-session, cross-tool memory** — the same context in Claude, Cursor, and Copilot rather than siloed per app.
- **Agentic / project memory** — agents capture decisions, patterns, and postmortems during work and recall them in future projects (e.g., as the long-term "L3" memory tier for the **Plan Forge** execution system).
- **Personal/team knowledge** — preferences, prior decisions, and people surfaced semantically.
- **Auditable memory** — provenance lets you verify where a memory came from.
- **Knowledge-base chat** — workable by chunking articles into thoughts tagged with a stable slug, then using `search_thoughts`; note this adapts a memory tool to a document-retrieval job (see comparison below).

---

## Open Brain vs traditional RAG

Open Brain *is* a RAG implementation; the difference is framing and write semantics, not a different retrieval paradigm.

| Dimension | Traditional RAG | Open Brain (memory) |
|---|---|---|
| Unit of storage | Document chunks (passages) | "Thoughts" (facts/decisions) |
| Write pattern | Batch ingest of an authored corpus | Continuous incremental capture |
| Direction | Read-mostly over fixed corpus | Read-write; agent writes back |
| Integration | Usually one app | One backend across many clients (MCP) |
| Retrieval | Often hybrid search + rerankers + citations | Vector + metadata filter (simpler) |
| Best for | External authoritative knowledge | Evolving personal/agent context |

**Decision rule:** if you're modeling an external body of knowledge that exists independently of your conversations → **RAG**. If you're modeling the running context of your own work and decisions → **memory**.

### When traditional RAG is preferable
- Large, relatively static, authoritative corpora (product docs, legal/compliance, research, support KB).
- Answers must cite and trace back to specific source passages.
- High precision/recall at scale; rerankers and hybrid search justified.
- A single app where you own the document lifecycle.
- (A "chat with my KB articles" task leans RAG — Open Brain can do it, but a purpose-built RAG setup or a framework like LlamaIndex is the more natural fit as the corpus grows.)

### When Open Brain-style memory gives better results
- Accumulated, evolving context: decisions, preferences, project history, who-said-what.
- Cross-session and cross-tool continuity.
- Continuous incremental capture rather than a fixed corpus.
- Agentic workflows where the assistant both reads and writes context.
- Privacy-sensitive, low-ops self-hosting.

### They're complementary
Strong systems use both: RAG over the authoritative document corpus ("what does the documentation say") plus a memory layer ("what did we decide, what does this user prefer, what happened last time").

---

## Similar tools

- **Mem0** — closest peer; hybrid vector-graph memory with multi-level (user/session/agent) memory and MCP support. Lower-friction if you'd rather not self-host.
- **LlamaIndex** — heavier, do-everything RAG framework; composable buffers and semantic search. More than needed for simple memory.
- **Khoj** — local-first personal search and knowledge graphs; good when privacy/local search matters more than agentic automation.

---

## Deployment options

Five paths, same tools and clients:

| Path | Best for | Cost | Level |
|---|---|---|---|
| Docker Desktop dev box | Win/Mac laptop, fully local & private (Ollama on host) | $0 | Beginner |
| Docker Compose (Linux) | Headless server, NAS, Raspberry Pi, VPS | $0–5 | Beginner |
| Cheap hosted | Always-on (Supabase/Neon + Fly.io) | $0–5/mo | Beginner |
| Kubernetes | Homelab / on-prem cluster, GPU Ollama | $0 (own hw) | Intermediate |
| Azure (managed) | One-command Bicep: Container Apps + PostgreSQL Flex + Azure OpenAI | ~$15–20/mo | Intermediate |

Provider-agnostic: the Azure architecture maps to AWS (ECS / RDS / Bedrock) and GCP (Cloud Run / Cloud SQL / Vertex AI). Setup can be done via a paste-in AI prompt, a setup wizard script, or manually; a 60-second smoke test (`verify.ps1`/`.sh`) confirms it works.

---

## Limitations / things to watch

- **You self-host infrastructure** — a server plus Postgres (ideally a local embedder). Best for people comfortable with Docker who value owning their data over a turnkey service.
- **Not a turnkey document-RAG product** — for KB/document use you supply the chunking and sync logic yourself.
- **Simpler retrieval** than mature RAG stacks — no built-in reranking, hybrid search, or query rewriting.
- **Chunk documents** if you store articles — one thought = one embedding, so whole-article thoughts retrieve poorly.

---

## Quick-reference facts

- **Ports:** MCP 8080, REST 8000 — **Health probe:** `GET /health`
- **Embedding dimension:** 768
- **Embedders:** Ollama (local/free), OpenRouter (cloud), Azure OpenAI
- **Storage:** PostgreSQL + pgvector, single `thoughts` table, HNSW (vector) + GIN (metadata) indexes
- **Clients:** any MCP-compatible (Claude, Claude Code, Cursor, Copilot, ChatGPT, Gemini, Grok, Windsurf)
- **Provenance (v0.7.0+):** Hallmark envelope — contentHash, codeHash, phase, tool
- **Companion project:** Plan Forge (Open Brain serves as its long-term memory tier)

# AI Domain Knowledge Base

This repository is a personal AI ecosystem wiki inspired by Andrej Karpathy's [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) pattern.

The basic idea is simple: instead of treating a folder of documents as passive files for one-off retrieval, an LLM agent incrementally turns those documents into a persistent, interlinked Markdown wiki. Raw sources stay intact. The wiki becomes the maintained synthesis layer. Agent instructions define the rules that keep the process disciplined.

In other words, this is not just "chat over files." It is a compounding knowledge artifact: each ingest can update concept pages, entity pages, cross-links, contradictions, index entries, and logs so future queries start from organized knowledge instead of rediscovering the same material again.

## Structure

```text
.
├── source/        # Raw source documents; read-only input corpus for agents
├── wiki/          # Maintained Markdown wiki generated and updated from sources
├── AGENTS.md      # Primary operating schema for AI agents
├── CLAUDE.md      # Companion agent instruction file for Claude-style tools
├── README.md      # Human-facing overview of the repository
└── wiki-roadmap.md # Planning notes for future wiki growth
```

## The Three Layers

### 1. `source/`

`source/` contains the original materials: articles, notes, summaries, references, and other documents about AI. These files are the source of truth. Agents may read them, but should not rewrite them during normal wiki maintenance.

When a new document is added here, the expected workflow is to ingest it into the wiki: identify the important concepts, entities, models, techniques, papers, and tools, then update the relevant pages in `wiki/`.

### 2. `wiki/`

`wiki/` is the curated knowledge layer. It contains short, cross-linked Markdown pages grouped by category:

- `overview.md` - top-level map of the AI ecosystem
- `index.md` - catalog of all wiki pages, read first when answering questions
- `log.md` - append-only history of ingests, queries, and lint passes
- `subfields/` - NLP, computer vision, robotics, speech, recommender systems, and related areas
- `concepts/` - core ideas such as machine learning, deep learning, LLMs, embeddings, hallucination, and groundedness
- `architectures/` - Transformer, CNN, diffusion models, GANs, RNN/LSTM, autoencoders, MLPs
- `techniques/` - prompting, RAG, fine-tuning, RLHF, quantization, agents, guardrails, evals
- `models/` - GPT, Claude, Gemini, Llama, BERT, Stable Diffusion, DALL-E, DeepSeek, and others
- `orgs/`, `people/`, `papers/`, `tools/`, `reference/` - entity and reference pages that make the graph navigable

Pages are intentionally shallow. The goal is orientation and connection, not full textbook depth. When a topic needs deeper treatment, the wiki should link out or create a stub rather than turning one page into a long essay.

### 3. Agent Instructions

Agent instruction files define how AI agents should work with the repository.

- `AGENTS.md` is the load-bearing schema for this wiki. It defines page types, directory conventions, ingest rules, query behavior, lint checks, and invariants.
- `CLAUDE.md` exists for compatibility with Claude-style coding agents.

The most important invariant is: agents read from `source/`, write to `wiki/`, update `wiki/index.md`, and append activity to `wiki/log.md`.

## Core Workflows

### Ingest

Add a new document to `source/`, then ask an agent to ingest it. A good ingest should update several small wiki pages rather than create one giant summary. It should also update `wiki/index.md` and append an entry to `wiki/log.md`.

### Query

Ask questions against the wiki. Agents should start from `wiki/index.md`, follow the relevant links, and synthesize answers from the maintained wiki pages. Useful new syntheses can be filed back into the wiki when they add durable structure.

### Lint

Periodically ask an agent to lint the wiki. The lint pass should look for stale claims, missing links, orphan pages, missing frontmatter, pages that have grown too long, taxonomy drift, and topics that deserve new stubs.

## Design Principles

- Keep raw sources immutable.
- Keep wiki pages short, link-rich, and easy to scan.
- Prefer breadth-first mapping over deep exposition.
- Use Obsidian-style `[[wikilinks]]` inside wiki pages.
- Keep tags in YAML frontmatter, not inline hashtags.
- Distinguish models from products and apps.
- Treat `wiki/index.md` as the map and `wiki/log.md` as the timeline.
- Let agents handle bookkeeping, while humans curate sources and steer judgment.

## Current Scope

This wiki is focused on the AI ecosystem: subfields, history, concepts, architectures, techniques, models, organizations, people, papers, tools, and practical reference material. It is intended as a breadth-first personal map for learning and orientation, not a comprehensive ML textbook.

# AI Ecosystem Wiki — Schema

A breadth-first personal map of the AI ecosystem. Practitioner-oriented: favor how things are used over the underlying theory/math.

## Purpose

Not a textbook — a map. Every page orients and connects; none teaches in depth. When a topic wants depth, it becomes a separate focused KB; this wiki keeps a stub that links out.

## Directory layout

```
wiki/
  index.md           # catalog of every page — update on every ingest, read first when answering
  log.md             # append-only activity log (format: ## [YYYY-MM-DD] ingest | Title)
  overview.md        # top-level AI ecosystem map
  subfields/         # NLP, CV, RL, speech, robotics, recommenders, multimodal
  history/           # AI history timeline
  concepts/          # machine learning, deep learning, generative AI, LLMs, classical ML (stub)
  architectures/     # transformer, CNN, RNN/LSTM, GAN, diffusion, autoencoder, MLP
  techniques/        # prompting, RAG, fine-tuning, RLHF, LoRA, quantization, agents, pretraining
  models/            # GPT, Codex, Gemini, Llama, AlexNet, BERT, Stable Diffusion, DALL·E, DeepSeek
  orgs/              # OpenAI, Anthropic, Google DeepMind, Meta AI, Mistral, Hugging Face
  people/            # Hinton, LeCun, Bengio, Sutton, Turing, Karpathy, McCarthy, Sutskever
  papers/            # Attention Is All You Need, The Bitter Lesson, AlexNet/ImageNet
  tools/             # ChatGPT, Ollama, LangChain, Open Brain, LM Studio
  reference/         # reading lists and external resources
source/              # immutable raw source documents — read only, never edit
```

## Page types

**Entity pages** (orgs, people, models, papers) — hubs that make the graph dense. Build lightly but early. Keep the **model** distinct from the **app** (GPT-4 the model vs. ChatGPT the product).

**Concept pages** (subfields, techniques, architectures, history, concepts) — the map. Subfields are the top-priority orientation layer; build them first.

## Conventions (load-bearing — follow these strictly)

1. **Pages stay shallow** — ~150 words target. When a topic wants more, **link out, don't expand.** A page's job is to orient and connect, not to teach in full.
2. **Cross-link aggressively** — every page should link to the entities and concepts it touches. Use `[[filename]]` wikilinks (Obsidian-compatible). The value is the connections, not the content.
3. **Keep tags as metadata** — use YAML frontmatter (`type` plus `tags`) for Foam filtering. Do not mirror every wikilink as an inline hashtag; it makes pages hard to read. Body prose should use wikilinks, not inline `#tags`.
4. **Use page-level tags only** — every wiki page except `wiki/index.md` and `wiki/log.md` should start with frontmatter: `type` is the page category (`concept`, `model`, `tool`, etc.); `tags` are compact page-level facets such as the page slug, category, and a few durable topics. Do not tag every mentioned link.
5. **Classical ML is a stub here** — linear regression, SVMs, decision trees, etc. belong in a separate focused KB (practice notebook). In this wiki: a one-paragraph stub only, no worked examples or math.
6. **Default to breadth on ingest** — when a source is rich, prefer touching/updating several existing pages over writing one long new one.
7. **Flag, don't bury, deep material** — if a source pulls toward depth, note it as a candidate for a focused KB rather than expanding the general page.

## Deferred categories (stub-only until explicitly requested)

Math & theory foundations · datasets & benchmarks · evaluation metrics · AI safety & alignment · MLOps / infrastructure · classical ML algorithm details

## Operations

### Ingest
1. Read the source file in `source/`.
2. Identify key concepts, entities, and techniques mentioned.
3. Create or update pages across multiple categories — breadth over depth.
4. Add or update page frontmatter (`type`, `tags`) on every created or touched wiki page; keep tags in metadata only, never inline after wikilinks.
5. Update `wiki/index.md` with any new pages.
6. Append a log entry to `wiki/log.md`:
   `## [YYYY-MM-DD] ingest | Source Title`

### Contradiction handling
When new material conflicts with existing wiki pages, do not quietly overwrite the older claim. Flag the contradiction in the relevant page, cite the conflicting wiki/source context, and decide whether to revise the page, keep both claims with qualification, or mark the issue for later research.

### Query
1. Start from `wiki/index.md`, follow links to relevant pages.
2. Synthesize a cited answer referencing wiki page names.
3. If the answer reveals a useful new cross-topic connection, file it back as a wiki page.
4. Append a query log entry to `wiki/log.md` when the query produces durable wiki changes or an important synthesis:
   `## [YYYY-MM-DD] query | Question or Topic`

### Lint
Check for: pages past the shallow target (trim or split), orphan pages with no inbound links, important concepts lacking stubs, missing cross-references between related subfields/techniques, missing or bloated frontmatter tags, inline hashtags in body prose, stale claims about fast-moving areas (models, tools), and gaps a quick web/source search could fill. Surface "next topics to map."

Append a lint log entry to `wiki/log.md` after each lint pass:
`## [YYYY-MM-DD] lint | Scope`

## Index and log

`wiki/index.md` is the catalog of every wiki page. Keep it grouped by category and give each page a one-line summary so agents can orient before reading individual pages.

`wiki/log.md` is append-only. Log ingests always; log queries when they produce durable wiki changes or important synthesis; log every lint pass.

## Key invariants

- The LLM reads `source/` but **never** writes to it.
- `wiki/log.md` is append-only — never delete or edit past entries.
- Model ≠ app: keep model pages (GPT-4) separate from app/product pages (ChatGPT).
- This is `wiki/` only — the general map. Focused KBs for deep topics live elsewhere.

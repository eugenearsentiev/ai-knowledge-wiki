---
type: concept
tags:
  - "concept"
  - "embeddings"
  - "transformer"
  - "rag"
  - "context-window"
  - "bert"
  - "recommender-systems"
  - "open-brain"
---

# Embeddings

Numerical vector representations of text, images, audio, or other data. Embeddings place similar items near each other in vector space, making them useful for search, clustering, recommendations, and retrieval.

**In LLM systems** — tokens start as embedding vectors before passing through [[transformer|Transformer]] layers. Separate encoder-style models also create document and query embeddings for semantic search.

**RAG role** — [[rag|RAG]] usually embeds documents into a vector database, embeds the user's query, retrieves nearby chunks, then injects those chunks into the [[context-window|context window]] for generation.

**Architecture link** — [[bert|BERT]]-style encoder models are especially common for embeddings because they read the whole input bidirectionally and produce useful representations for similarity.

**Links** — [[rag|RAG]], [[bert|BERT]], [[transformer|Transformer]], [[recommender-systems|Recommender systems]], [[open-brain|Open Brain]].

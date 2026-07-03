---
type: model
tags:
  - "model"
  - "bert"
  - "transformer"
  - "pretraining"
  - "nlp"
  - "fine-tuning"
  - "gpt"
  - "rag"
  - "google-deepmind"
---

# BERT (Bidirectional Encoder Representations from Transformers)

An encoder-only [[transformer|Transformer]] model released by Google in 2018. BERT introduced **masked language modeling** as a [[pretraining|pretraining]] objective: randomly mask some tokens, train the model to predict them using context from both directions simultaneously.

**Impact** — set new state-of-the-art across a wide range of [[nlp|NLP]] benchmarks and popularized the pretrain → [[fine-tuning|fine-tune]] paradigm for language understanding tasks.

**Encoder vs. decoder** — BERT is an encoder model (excellent at understanding, classification, and embeddings); the [[gpt|GPT]] family is decoder-only (generative). Both patterns descend from the [[transformer|Transformer]] paper.

**Legacy** — inspired a large family of variants (RoBERTa, DistilBERT, ALBERT) and anchors embedding-based search and [[rag|RAG]] pipelines today. Most text embedding models trace back to BERT-style pretraining.

**Links** — [[nlp|NLP]], [[transformer|Transformer]], [[pretraining|Pretraining]], [[rag|RAG]], [[google-deepmind|Google]].

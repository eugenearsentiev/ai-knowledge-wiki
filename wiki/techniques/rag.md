---
type: technique
tags:
  - "technique"
  - "rag"
  - "llm"
  - "embeddings"
  - "context-window"
  - "inference"
  - "fine-tuning"
  - "langchain"
  - "open-brain"
  - "prompting"
  - "agents-tool-use"
  - "hallucination"
  - "faithfulness"
  - "groundedness"
  - "context-recall"
  - "rag-evaluation"
---

# Retrieval-Augmented Generation (RAG)

Fetch relevant documents at query time and inject them into the [[llm|LLM]]'s context so answers draw on external or up-to-date knowledge beyond what the model learned during training.

**Why it matters** — LLMs have a training cutoff and no access to private data. RAG bridges this by embedding a corpus, retrieving relevant chunks, injecting them into the [[context-window|context window]], and generating a grounded answer.

**Pipeline** — index documents → embed query → retrieve chunks → inject into prompt → generate during [[inference|inference]].

**Reliability lens** — RAG reduces [[hallucination]], but bad chunking, missing retrieval, irrelevant context, context conflicts, or [[citation-mismatch|citation mismatch]] can still produce unfaithful answers. Track [[faithfulness]], [[groundedness]], and [[context-recall]] with [[rag-evaluation|RAG evaluation]].

**vs. fine-tuning** — RAG adds knowledge at inference time (flexible, updatable, no retraining); [[fine-tuning|fine-tuning]] bakes knowledge into weights (faster inference, less flexible). Often complementary.

**Key tools** — [[langchain|LangChain]], LlamaIndex. [[open-brain|Open Brain]] uses a RAG architecture as its memory layer.

**Links** — [[llm|LLM]], [[prompting|Prompting]], [[fine-tuning|Fine-tuning]], [[agents-tool-use|Agents]], [[open-brain|Open Brain]], [[hallucination]], [[faithfulness]], [[groundedness]], [[rag-evaluation]].

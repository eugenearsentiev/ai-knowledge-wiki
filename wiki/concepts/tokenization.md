---
type: concept
tags:
  - "concept"
  - "tokenization"
  - "llm"
  - "context-window"
  - "inference"
  - "prompting"
---

# Tokenization

The first step in most [[llm|LLM]] workflows: convert human text into small machine-readable chunks called tokens. Tokens may be whole words, word fragments, punctuation, spaces, or code symbols; the model sees token IDs, not raw characters.

**Why it matters** — tokens are the unit of cost, [[context-window|context window]] length, and generation. A long document, multilingual text, or verbose system prompt can become expensive because every input and output token is counted.

**Common approach** — modern LLM tokenizers often use byte-pair-style vocabularies that merge frequent character sequences into reusable chunks. This makes common words efficient while still allowing rare words, names, code, and symbols to be represented.

**Practitioner consequence** — tokenization explains some odd failures, such as weak character counting, because the model may reason over word pieces rather than individual letters.

**Links** — [[llm|LLM]], [[context-window|Context window]], [[inference|Inference]], [[prompting|Prompting]].

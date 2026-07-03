---
type: concept
tags:
  - "concept"
  - "sampling"
  - "llm"
  - "inference"
  - "prompting"
  - "agents-tool-use"
---

# Sampling

The generation-time process for choosing the next token from a model's probability distribution. An [[llm|LLM]] usually has many plausible next tokens; sampling settings decide whether it behaves predictably or explores more varied options.

**Temperature** — the best-known sampling dial. Low temperature concentrates probability on the most likely tokens, making output more consistent. Higher temperature flattens the distribution, increasing variety and the risk of unexpected or wrong turns.

**Related controls** — top-k limits selection to the k most likely tokens; top-p (nucleus sampling) keeps the smallest token set whose cumulative probability reaches a threshold.

**Practitioner use** — use low temperature for extraction, classification, code, and evals; raise it for brainstorming or creative writing where diversity is useful.

**Links** — [[inference|Inference]], [[llm|LLM]], [[prompting|Prompting]], [[agents-tool-use|Agents and tool use]].

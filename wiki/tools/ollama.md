---
type: tool
tags:
  - "tool"
  - "ollama"
  - "llm"
  - "llama"
  - "mistral"
  - "quantization"
  - "lm-studio"
---

# Ollama

A tool for running open-weight [[llm|LLMs]] locally on Mac, Linux, or Windows. Provides a simple CLI and API to download and run models like [[llama|Llama]], [[mistral|Mistral]], and others with a single command (`ollama run llama3`).

**Why it matters** — removes most of the friction from local LLM deployment. No cloud API needed; models run on-device for privacy, offline use, and zero per-query cost. Works with [[quantization|quantized]] models (GGUF format) to fit large models into consumer GPU or CPU memory.

**How it works** — wraps llama.cpp (a C++ inference engine) with a user-friendly interface and model library. Exposes a local REST API compatible with the OpenAI API format (drop-in for many apps).

**Model library** — includes [[llama|Llama]], [[mistral|Mistral]], Gemma, Phi, Qwen, and hundreds of fine-tuned variants.

**Compared to [[lm-studio|LM Studio]]** — CLI-first and developer-focused; LM Studio is GUI-first.

**Links** — [[llm|LLM]], [[llama|Llama]], [[quantization|Quantization]], [[mistral|Mistral]], [[lm-studio|LM Studio]].

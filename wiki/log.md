# Wiki Log

Append-only chronological record of ingests, queries, and lint passes.

---

## [2026-06-11] ingest | Bulk initial ingest (all source files)

Sources processed:
- `01-ai-ecosystem-overview.md` — AI nesting, subfields, major players, practitioner stack
- `02-history-of-ai.md` — Full AI history timeline from 1940s to present
- `03-machine-learning-foundations.md` — ML paradigms, classical algorithms, core concepts
- `04-neural-networks-and-architectures.md` — NN mechanics, major architectural families
- `05-llm-and-generative-ai-landscape.md` — LLMs, generative AI, core techniques, tools/apps
- `data-science-books.md` — Curated data science reading list
- `open-brain-reference.md` — Open Brain persistent memory tool reference

Pages created:
- `wiki/overview.md` + `wiki/index.md` + `wiki/log.md`
- Subfields (7): nlp, computer-vision, reinforcement-learning, speech, robotics, recommender-systems, multimodal-ai
- History (1): timeline
- Concepts (5): machine-learning, deep-learning, generative-ai, llm, classical-ml
- Architectures (7): transformer, cnn, rnn-lstm, gan, diffusion-models, autoencoder, mlp
- Techniques (8): prompting, rag, fine-tuning, rlhf, lora, quantization, agents-tool-use, pretraining
- Models (9): gpt, claude, gemini, llama, stable-diffusion, dalle, alexnet, bert, deepseek
- Orgs (6): openai, anthropic, google-deepmind, meta-ai, mistral, hugging-face
- People (8): geoffrey-hinton, yann-lecun, yoshua-bengio, rich-sutton, alan-turing, andrej-karpathy, john-mccarthy, ilya-sutskever
- Papers (3): attention-is-all-you-need, bitter-lesson, alexnet-imagenet
- Tools (5): chatgpt, ollama, langchain, open-brain, lm-studio
- Reference (1): data-science-books

Total: 71 pages created. Wiki initialized.

## [2026-06-18] ingest | How LLMs Work at the Architectural Level

Source processed:
- `how-llms-work.md` — Tokens, Transformers, context windows, temperature/sampling, parameters, inference loop

Pages created:
- `wiki/concepts/tokenization.md`
- `wiki/concepts/context-window.md`
- `wiki/concepts/inference.md`
- `wiki/concepts/sampling.md`
- `wiki/concepts/parameters.md`
- `wiki/concepts/embeddings.md`

Pages updated:
- `wiki/concepts/llm.md`
- `wiki/architectures/transformer.md`
- `wiki/techniques/rag.md`
- `wiki/techniques/prompting.md`
- `wiki/index.md`

## [2026-06-18] query | Model classifications

Pages created:
- `wiki/reference/model-classifications.md` — Practical model classification axes: LLMs, VLMs, SLMs, MoE, embedding models, classifiers, openness, size, and deployment

Pages updated:
- `wiki/index.md`

## [2026-06-18] query | Foundation models

Pages updated:
- `wiki/reference/model-classifications.md` — Added foundation models as a broad base-model category connected to LLMs, VLMs, fine-tuning, RAG, and task-specific adaptation

## [2026-06-18] query | Prompt engineering guide

Pages created:
- `wiki/reference/prompt-engineering-guide.md` — Practical guide explaining prompt engineering and common techniques with examples

Pages updated:
- `wiki/index.md`

## [2026-06-18] query | Removed prompt engineering guide

Pages removed:
- `wiki/reference/prompt-engineering-guide.md`

Pages updated:
- `wiki/index.md`

## [2026-06-18] ingest | Prompt Engineering Guide

Source processed:
- `prompt-engineering-guide.md` — Prompt engineering overview, prompt structure, common techniques, examples, and pitfalls

Pages created:
- `wiki/techniques/zero-shot-prompting.md`
- `wiki/techniques/few-shot-prompting.md`
- `wiki/techniques/chain-of-thought-prompting.md`
- `wiki/techniques/structured-output-prompting.md`
- `wiki/techniques/prompt-templates.md`

Pages updated:
- `wiki/techniques/prompting.md`
- `wiki/index.md`

## [2026-06-23] ingest | Spec-Driven Development Related Articles Summary

Source processed:
- `sdd-related-articles-summary.md` — GitHub Spec Kit, Kiro, EARS, OpenAPI, and 2026 SDD research themes

Pages created:
- `wiki/techniques/spec-driven-development.md`
- `wiki/techniques/ears-requirements.md`
- `wiki/tools/github-spec-kit.md`
- `wiki/tools/kiro.md`
- `wiki/tools/openapi.md`
- `wiki/reference/sdd-reading-list.md`

Pages updated:
- `wiki/techniques/agents-tool-use.md`
- `wiki/techniques/prompting.md`
- `wiki/techniques/structured-output-prompting.md`
- `wiki/index.md`

## [2026-06-26] query | Vibe coding tools

Pages created:
- `wiki/tools/vibe-coding-tools.md` — Shallow map of AI app builders and coding-agent tools

Pages updated:
- `wiki/index.md`

## [2026-07-01] ingest | A Product Manager's Guide to AI Model Evaluations

Source processed:
- `model-evals.md` — LLM eval lifecycle: static benchmarks, human preference tests, LLM-as-judge automation, process vs. outcome evals, risk audits, and vendor analysis

Pages created:
- `wiki/reference/model-evals.md`
- `wiki/reference/ai-benchmarks.md`
- `wiki/techniques/llm-as-judge.md`

Pages updated:
- `wiki/concepts/llm.md`
- `wiki/techniques/rlhf.md`
- `wiki/reference/model-classifications.md`
- `wiki/index.md`

## [2026-07-01] ingest | A Product Manager's Guide to LLM Hallucinations

Source processed:
- `pm-guide-to-llm-hallucinations.md` — Product-oriented map of hallucination types, root causes, evaluation dimensions, and mitigation patterns

Pages created:
- `wiki/concepts/hallucination.md`
- `wiki/concepts/factuality.md`
- `wiki/concepts/faithfulness.md`
- `wiki/techniques/guardrails.md`

Pages updated:
- `wiki/concepts/llm.md`
- `wiki/techniques/rag.md`
- `wiki/techniques/prompting.md`
- `wiki/techniques/agents-tool-use.md`
- `wiki/reference/model-evals.md`
- `wiki/techniques/llm-as-judge.md`
- `wiki/index.md`

## [2026-07-01] ingest | The RAG Hallucination Nexus: Diagnostics and Defenses

Source processed:
- `RAG-hallucination-nexus-diagnostics-and-defenses.md` — RAG-specific hallucination pathways, diagnostics, faithfulness/groundedness evaluation, and real-time gates

Pages created:
- `wiki/concepts/groundedness.md`
- `wiki/concepts/context-recall.md`
- `wiki/concepts/citation-mismatch.md`
- `wiki/techniques/rag-evaluation.md`

Pages updated:
- `wiki/concepts/hallucination.md`
- `wiki/concepts/faithfulness.md`
- `wiki/techniques/rag.md`
- `wiki/reference/model-evals.md`
- `wiki/techniques/guardrails.md`
- `wiki/techniques/llm-as-judge.md`
- `wiki/index.md`

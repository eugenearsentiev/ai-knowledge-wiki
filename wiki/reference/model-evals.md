---
type: reference
tags:
  - "reference"
  - "model-evals"
  - "llm"
  - "ai-benchmarks"
  - "llm-as-judge"
  - "rlhf"
  - "hallucination"
  - "factuality"
  - "faithfulness"
  - "groundedness"
  - "rag-evaluation"
---

# Model Evals

Model evaluations are structured checks for whether an AI model is good enough for a product use case. They complement QA, A/B tests, and KPI tracking because [[llm|LLMs]] are open-ended, probabilistic, and sensitive to prompts.

**Static benchmarks** such as [[ai-benchmarks|MMLU and HELM]] give baseline capability signals: knowledge breadth, accuracy, calibration, robustness, bias, toxicity, and efficiency.

**Human preference evals** compare outputs side by side, often for tone, helpfulness, formatting, and subjective quality. The same preference signal also powers [[rlhf|RLHF]].

**Automated evals** run test sets in development pipelines. [[llm-as-judge|LLM-as-judge]] grading is useful for catching prompt or model regressions, but should be calibrated against human agreement.

**Hallucination evals** focus on [[factuality]], [[faithfulness]], [[groundedness]], attribution, [[context-recall]], and answer relevance. Text-overlap metrics rarely catch unsupported claims by themselves.

**RAG evals** isolate where the failure happened: retrieval, prompt construction, generation, citation, or guardrail. See [[rag-evaluation]].

**Risk evals** red-team dangerous capabilities, misuse potential, and alignment failures before deployment. This page stays text-model focused; multimodal, system-level, and societal-risk evals need separate focused notes.

**Links** — [[llm]], [[ai-benchmarks]], [[llm-as-judge]], [[rlhf]], [[model-classifications]], [[hallucination]], [[factuality]], [[faithfulness]], [[groundedness]], [[rag-evaluation]].

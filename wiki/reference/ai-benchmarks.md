---
type: reference
tags:
  - "reference"
  - "ai-benchmarks"
  - "model-evals"
  - "llm"
  - "model-classifications"
---

# AI Benchmarks

AI benchmarks are standardized tests used to compare model capabilities. They are useful starting points for [[model-evals|model evals]], but not a substitute for product-specific test sets.

**MMLU** measures broad academic and professional knowledge across many subject areas. It helps identify general strengths and lopsided capability gaps.

**HELM** frames evaluation as a dashboard, not a single score: accuracy, calibration, robustness, fairness, bias, toxicity, and efficiency all matter.

**Chatbot Arena-style evaluation** uses pairwise human preference votes on anonymous model responses. It is closer to real usage than static tests, but reflects the prompts and voters who show up.

For product decisions, benchmark results should be filtered through task fit, cost, latency, context needs, safety requirements, and deployment constraints. See [[model-classifications]] for adjacent model-selection axes.

**Links** — [[model-evals]], [[llm]], [[model-classifications]].

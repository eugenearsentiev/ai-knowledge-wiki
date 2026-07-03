---
type: reference
tags:
  - "reference"
  - "sdd-reading-list"
  - "spec-driven-development"
  - "kiro"
  - "ears-requirements"
  - "openapi"
  - "github-spec-kit"
  - "agents-tool-use"
---

# SDD Reading List

A compact reading map for [[spec-driven-development|spec-driven development]] in AI-assisted coding.

Start with product/tooling sources: GitHub's Spec Kit blog and repository explain the specify -> plan -> tasks -> implement workflow; [[kiro|Kiro]] docs show a lightweight three-file spec model using [[ears-requirements|EARS]] requirements.

Then read adjacent specification practices: EARS for structured natural-language requirements and [[openapi|OpenAPI]] for a mature machine-readable API contract ecosystem.

The 2026 research thread frames SDD as a response to AI coding risks: hallucinated APIs, weak repository context, security defects, long review cycles, and unreliable generated code. The useful distinction is spec-first, spec-anchored, and spec-as-source. Spec-as-source is the most ambitious and least proven.

**Takeaway** - SDD should scale with risk. Use lightweight specs for small changes; use stronger governance for security, compliance, cross-component, or long-lived work.

**Links** - [[spec-driven-development]], [[github-spec-kit]], [[kiro]], [[openapi]], [[agents-tool-use]].

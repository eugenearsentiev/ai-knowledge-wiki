---
type: technique
tags:
  - "technique"
  - "spec-driven-development"
  - "llm"
  - "github-spec-kit"
  - "kiro"
  - "ears-requirements"
  - "agents-tool-use"
  - "prompting"
  - "structured-output-prompting"
  - "openapi"
---

# Spec-Driven Development

**Spec-driven development (SDD)** is a workflow where explicit requirements, design notes, and task plans guide AI-assisted implementation. In the AI coding context, it is a response to vague prompting: instead of asking an [[llm|LLM]] agent to "build X," the team first captures behavior, constraints, success criteria, and checkpoints.

Common SDD flows move through specify -> plan -> tasks -> implement. [[github-spec-kit|GitHub Spec Kit]] and [[kiro|Kiro]] both use this shape, often with [[ears-requirements|EARS-style requirements]] and agent-executable task lists.

SDD is most useful for product behavior, cross-component changes, security-sensitive work, and brownfield features where repository context matters. It can be too heavy for small low-risk edits.

**Watchouts** - specs can become documentation theater if they are verbose, stale, or not grounded in the real codebase. The strongest versions connect specs to tests, reviews, and implementation evidence.

**Links** - [[agents-tool-use]], [[prompting]], [[structured-output-prompting]], [[github-spec-kit]], [[kiro]], [[ears-requirements]], [[openapi]].

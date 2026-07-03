---
type: tool
tags:
  - "tool"
  - "kiro"
  - "spec-driven-development"
  - "ears-requirements"
  - "agents-tool-use"
  - "github-spec-kit"
---

# Kiro

**Kiro** is an AI development environment built around [[spec-driven-development|spec-driven development]]. It tries to bridge fast AI prototyping and production-ready software by turning prompts into requirements, design notes, tasks, and auditable implementation history.

A Kiro spec has three main files: `requirements.md`, `design.md`, and `tasks.md`. Requirements use [[ears-requirements|EARS-style acceptance criteria]]; design captures architecture and implementation considerations; tasks sequence the work into small executable pieces.

Kiro also includes hooks: event-driven agent automations that can run on file changes or manual triggers. These can refresh docs, enforce standards, update tests, or scan for issues.

**Why it matters** - Kiro represents the productized version of AI SDD: specs are not just documents, but the coordination layer between humans, code, and agents.

**Links** - [[spec-driven-development]], [[ears-requirements]], [[agents-tool-use]], [[github-spec-kit]].

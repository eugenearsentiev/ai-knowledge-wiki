---
type: technique
tags:
  - "technique"
  - "ears-requirements"
  - "spec-driven-development"
  - "kiro"
  - "structured-output-prompting"
  - "prompt-templates"
---

# EARS Requirements

**EARS** (Easy Approach to Requirements Syntax) is a lightweight way to write structured natural-language requirements. It predates modern AI coding, but it fits [[spec-driven-development|SDD]] because it gives both humans and agents clearer triggers, conditions, and expected behavior.

The core pattern is readable but constrained: "When [event], the system shall [expected behavior]." Variants cover always-on requirements, state-driven behavior, optional features, unwanted behavior, and combined conditions.

For AI-assisted work, EARS sits between free-form prompting and formal methods. It does not turn requirements into math, but it makes acceptance criteria easier to review, trace, and map to tests. [[kiro|Kiro]] uses EARS-style acceptance criteria in its spec workflow.

**Practical use** - write behavior first, avoid implementation detail in the requirement, and move architecture choices into a plan.

**Links** - [[spec-driven-development]], [[structured-output-prompting]], [[prompt-templates]], [[kiro]].

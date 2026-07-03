---
type: technique
tags:
  - "technique"
  - "structured-output-prompting"
  - "llm"
  - "agents-tool-use"
  - "ears-requirements"
  - "prompting"
  - "few-shot-prompting"
  - "rag"
---

# Structured Output Prompting

Ask an [[llm|LLM]] to return information in a specific shape: JSON, table, checklist, schema, bullets, or fields.

**Why it matters** — structure makes outputs easier to compare, automate, parse, and hand off to workflows. A product workflow might ask for `customer_name`, `problem`, `urgency`, and `requested_action` as JSON.

**Common uses** — data extraction, classification, workflow handoffs, API calls, analytics summaries, and repeatable reviews.

**Design rule** — specify both the fields and fallback behavior. For example: "Use `null` when the source does not contain the value" reduces guessing.

**Relation to tools** — structured output is especially important in [[agents-tool-use|agentic systems]], where one model response may become the input to another tool or API. [[ears-requirements|EARS requirements]] apply a similar idea to product behavior: constrained natural language that stays readable by humans but easier for tools and agents to validate.

**Links** — [[prompting]], [[few-shot-prompting]], [[agents-tool-use]], [[rag]], [[ears-requirements]].

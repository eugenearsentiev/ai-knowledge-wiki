---
type: technique
tags:
  - "technique"
  - "prompting"
  - "llm"
  - "zero-shot-prompting"
  - "few-shot-prompting"
  - "chain-of-thought-prompting"
  - "structured-output-prompting"
  - "prompt-templates"
  - "tokenization"
  - "context-window"
  - "sampling"
  - "rag"
  - "fine-tuning"
  - "agents-tool-use"
  - "spec-driven-development"
  - "hallucination"
---

# Prompting

Crafting the input text to steer an [[llm|LLM]]'s output. Prompt engineering is the practical discipline around this: define the task, provide context, set constraints, give examples when useful, and specify the output shape.

**Key patterns** — [[zero-shot-prompting|zero-shot]] (direct instruction), [[few-shot-prompting|few-shot]] (examples), [[chain-of-thought-prompting|chain-of-thought style]] (reasoning/rationale), role and audience prompts, constraints, delimiters, [[structured-output-prompting|structured output]], and [[prompt-templates|templates]].

**Runtime frame** — prompts consume [[tokenization|tokens]] inside the [[context-window|context window]]. Generation then depends on [[sampling|sampling]] settings such as temperature as well as the prompt itself.

**Why it matters** — the same model can behave very differently based on how it's prompted. Good prompts can unlock reasoning, reduce [[hallucination]], and control format. Bad prompts produce worse results even from powerful models.

**Limits** — prompting works within what the model already knows or what is provided in context. For new/private knowledge use [[rag|RAG]]; for durable new behavior use [[fine-tuning|fine-tuning]].

**Scales up** — in [[agents-tool-use|agentic]] systems, many LLM calls are chained; prompt engineering becomes essential for reliability at each step. For software work, [[spec-driven-development|spec-driven development]] turns prompts into reviewable requirements, plans, and tasks.

**Links** — [[llm|LLM]], [[rag|RAG]], [[fine-tuning|Fine-tuning]], [[agents-tool-use|Agents]], [[structured-output-prompting]], [[prompt-templates]], [[spec-driven-development]], [[hallucination]].

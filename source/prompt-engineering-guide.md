# Prompt Engineering Guide

Prompt engineering is the practice of writing instructions, context, examples, and output requirements so an [[llm|LLM]] produces a useful result. It does not change the model's weights. It steers the model at runtime through the text and data placed inside the [[context-window|context window]].

Good prompt engineering is less about magic phrases and more about clear task design: define the goal, provide relevant context, state constraints, show examples when needed, and specify the output format.

## Basic Prompt Structure

A strong prompt often includes:

```text
Role:
Who the model should act as.

Task:
What the model should do.

Context:
Relevant background, source material, audience, or constraints.

Output format:
The shape of the answer: bullets, table, JSON, email, summary, checklist.

Quality bar:
What good looks like, including tone, length, assumptions, and exclusions.
```

Example:

```text
Act as a product manager.
Summarize the customer feedback below into the top 5 pain points.
Group similar complaints together.
For each pain point, include severity, example quote, and suggested product action.
Return the result as a Markdown table.
```

## Zero-Shot Prompting

Zero-shot prompting asks the model to do a task directly without examples.

Use it when the task is simple or familiar.

Example:

```text
Summarize this article in 5 bullet points for a non-technical audience.
```

Best for:

```text
summaries
rewrites
brainstorming
classification with obvious labels
simple extraction
```

Limitation: if the task has a specific style or judgment standard, the model may guess what you want.

## Few-Shot Prompting

Few-shot prompting gives examples of the desired behavior before asking for the real answer.

Use it when the model needs to match a pattern, tone, label style, or decision rule.

Example:

```text
Classify each support ticket as Billing, Login, Bug, or Feature Request.

Example 1:
Ticket: "I was charged twice this month."
Category: Billing

Example 2:
Ticket: "The dashboard crashes when I export a report."
Category: Bug

Now classify:
Ticket: "I cannot access my account after resetting my password."
Category:
```

Best for:

```text
classification
style matching
data extraction
consistent formatting
domain-specific judgment
```

## Role Prompting

Role prompting tells the model what perspective to use.

Example:

```text
Act as a senior UX researcher.
Review this onboarding flow and identify where users may feel confused.
Focus on user intent, friction, and missing feedback.
```

Roles help shape vocabulary, priorities, and level of detail. They work best when paired with a concrete task.

Weak:

```text
Act as an expert and review this.
```

Better:

```text
Act as a B2B SaaS product manager.
Review this feature proposal for customer value, implementation risk, and launch readiness.
```

## Instruction Prompting

Instruction prompting gives explicit rules for how the model should perform the task.

Example:

```text
Rewrite the text below.

Rules:
- Keep the meaning unchanged.
- Use plain English.
- Remove jargon.
- Keep it under 120 words.
- Do not add new claims.
```

This is one of the most reliable prompt techniques. Clear constraints reduce ambiguity.

## Structured Output Prompting

Structured output prompting tells the model exactly how to format the response.

Example:

```text
Extract the following fields from the customer message:

- customer_name
- company
- problem
- urgency
- requested_action

Return the answer as JSON.
```

Example output shape:

```json
{
  "customer_name": "",
  "company": "",
  "problem": "",
  "urgency": "",
  "requested_action": ""
}
```

Best for:

```text
automation
data extraction
workflow handoffs
API calls
repeatable analysis
```

## Chain-of-Thought Style Prompting

Chain-of-thought prompting asks the model to reason before answering. In everyday use, it is often better to ask for a brief explanation or decision rationale rather than a long hidden reasoning trace.

Example:

```text
Compare these three roadmap options.
Think through customer impact, engineering effort, and strategic fit.
Then give a final recommendation with a short rationale.
```

Useful wording:

```text
Explain your decision briefly.
Show the key tradeoffs.
List the assumptions behind your answer.
```

Best for:

```text
prioritization
tradeoff analysis
planning
debugging
complex decisions
```

## Step-by-Step Prompting

Step-by-step prompting breaks a task into stages.

Example:

```text
Analyze this competitor landing page in three steps:

1. Identify the target customer.
2. Extract the main value propositions.
3. Suggest how our positioning should differ.
```

This helps when the task is broad and the model might otherwise jump straight to a shallow answer.

## Context-Rich Prompting

Context-rich prompting gives the model the background it needs to answer well.

Weak:

```text
Write a launch announcement.
```

Better:

```text
Write a launch announcement for a new AI meeting summary feature.
Audience: existing B2B customers.
Tone: clear, confident, not hype-heavy.
Key points: automatic summaries, action items, searchable history.
Avoid: claiming perfect accuracy.
Length: under 250 words.
```

The model can only use what is in the prompt, retrieved through [[rag|RAG]], available through tools, or already present in its training. For private or current information, provide the source material.

## Constraint Prompting

Constraint prompting tells the model what to avoid.

Example:

```text
Draft a customer-facing explanation.

Constraints:
- Do not mention internal systems.
- Do not blame the customer.
- Do not promise a specific fix date.
- Keep the tone calm and accountable.
```

Constraints are useful for brand, legal, safety, and product accuracy.

## Persona and Audience Prompting

Audience prompting adjusts depth, vocabulary, and tone.

Example:

```text
Explain vector databases to a product manager.
Avoid math.
Use a real-world analogy.
Include when they are useful and when they are overkill.
```

The same topic can be explained very differently for:

```text
executives
engineers
customers
sales teams
students
legal reviewers
```

## Delimiter Prompting

Delimiters separate instructions from source material. This reduces confusion.

Example:

~~~text
Summarize the source text between triple backticks.
Do not use outside information.

```
source text here
```
~~~

Common delimiters:

```text
triple backticks
XML-style tags
section headers
JSON fields
```

## Retrieval-Augmented Prompting

Retrieval-augmented prompting uses retrieved documents as context. This is the prompt layer of [[rag|RAG]].

Example:

```text
Answer the user's question using only the provided sources.
If the sources do not contain the answer, say so.
Cite the source title for each major claim.

Sources:
[retrieved chunks]

Question:
[user question]
```

Best for:

```text
knowledge bases
internal documentation
customer support
legal or policy lookup
fresh information
```

## Self-Critique Prompting

Self-critique prompting asks the model to review and improve its own answer.

Example:

```text
Draft the response.
Then review it for clarity, missing assumptions, and unsupported claims.
Finally, provide the improved version only.
```

This is useful for writing, analysis, and planning. For factual accuracy, it is better to combine critique with source checking or retrieval.

## Comparative Prompting

Comparative prompting asks the model to evaluate options side by side.

Example:

```text
Compare fine-tuning and RAG for a customer support chatbot.
Use a table with columns:
- Approach
- Best for
- Pros
- Cons
- When to choose it
```

Best for:

```text
product decisions
vendor comparison
architecture tradeoffs
roadmap options
prioritization
```

## Template Prompting

Template prompting creates reusable prompt patterns.

Example:

```text
You are analyzing a product feature.

Feature:
[feature name]

User problem:
[problem]

Target user:
[user]

Analyze:
1. User value
2. Business value
3. Implementation risk
4. Open questions
5. Recommendation
```

Templates are useful when a team needs consistent outputs across many inputs.

## Common Prompt Engineering Mistakes

Common mistakes include:

```text
asking vague questions
omitting audience or context
mixing multiple tasks without priority
not specifying the output format
asking for facts without providing sources
using examples that conflict with instructions
overloading the prompt with irrelevant context
expecting prompting to replace retrieval or fine-tuning
```

## Simple Prompt Checklist

Before sending a prompt, check:

```text
Is the task clear?
Is the audience clear?
Did I provide the needed context?
Did I specify the format?
Did I include constraints?
Did I say what to do when information is missing?
Would an example improve consistency?
```

## Practical Takeaway

Prompt engineering is the interface design layer for working with LLMs. Good prompts make the task, context, constraints, and output shape explicit. For simple tasks, direct instructions are enough. For repeatable or high-stakes tasks, use examples, structure, retrieval, validation, and clear fallback rules.

**Links** — [[prompting]], [[llm]], [[context-window]], [[tokenization]], [[rag]], [[fine-tuning]], [[agents-tool-use]].

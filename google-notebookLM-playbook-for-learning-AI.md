# Google NotebookLM Playbook for Learning AI

*Designed for an AI Product Manager transitioning into the AI domain.*

## Philosophy

NotebookLM is most powerful when you treat it as a **thinking partner**,
not a search engine or note-taking app.

The goal isn't to upload documents. The goal is to build a personal AI
mentor that only knows information you trust.

``` text
Raw Sources
    ↓
NotebookLM
    ↓
Your Understanding
```

Your job is not to remember everything. Your job is to repeatedly ask
good questions until concepts become intuitive.

## Beginner Mistakes

-   Uploading dozens of unrelated documents into one notebook.
-   Asking only for summaries.
-   Treating NotebookLM like a general chatbot.
-   Never testing your understanding.

Instead, create notebooks with a **single learning objective**.

Examples:

-   What are Embeddings?
-   How does RAG work?
-   How does Attention work?
-   What is MCP?
-   What is Fine-tuning?

## Learning Workflow

``` text
Choose Concept
      ↓
Collect Trusted Sources
      ↓
Upload to NotebookLM
      ↓
Build Mental Model
      ↓
Find Knowledge Gaps
      ↓
Generate Analogies
      ↓
Quiz Yourself
      ↓
Design Mini Project
      ↓
Connect to Previous Concepts
      ↓
Review Later
```

## Choosing Sources

Prefer:

-   Official documentation
-   Research papers
-   Engineering blogs
-   Vendor documentation
-   Your own notes

Aim for **5--15 high-quality sources**.

## Notebook Organization

### Concept Notebooks

One notebook per concept.

Examples: - Attention - Transformers - Embeddings - Vector Databases -
RAG - MCP

### Integration Notebooks

Create notebooks that connect concepts.

Examples: - How LLMs Work - How RAG Works - Building AI Agents

### Project Notebooks

Examples: - Local RAG Project - AI Chatbot - Coding Assistant

## Questions to Ask First

Instead of asking for a summary:

-   What problem does this solve?
-   Why was it invented?
-   What existed before it?
-   What are its limitations?
-   Explain it for an experienced Product Manager.

## Mental Models

Ask:

> Give me three different mental models for this concept.

## Find Knowledge Gaps

Ask:

-   What assumptions do these sources make?
-   Which prerequisite concepts are missing?
-   What misunderstandings do beginners usually have?

## Active Learning

``` text
Read
 ↓
Explain
 ↓
Challenge
 ↓
Quiz
 ↓
Mini Project
 ↓
Teach Back
 ↓
Review
```

## Prompt Library

-   Explain this concept assuming I'm an experienced Product Manager
    with limited ML knowledge.
-   Explain it at beginner, intermediate, and engineer levels.
-   Compare RAG, Fine-tuning, and Long Context.
-   Give five everyday analogies.
-   Test me without revealing the answers.
-   Create 30 flashcards.
-   What do beginners usually misunderstand?
-   What product decisions depend on understanding this concept?
-   Design the smallest Python project demonstrating this concept.

## AI Product Manager Workflow

1.  Understand the customer problem.
2.  Understand the technology.
3.  Learn trade-offs.
4.  Read implementation examples.
5.  Study APIs.
6.  Build a prototype.
7.  Reflect on product decisions.

## Example Learning Path (RAG)

1.  Collect trusted sources.
2.  Understand the problem RAG solves.
3.  Learn embeddings.
4.  Learn vector databases.
5.  Understand retrieval.
6.  Build a small RAG application.
7.  Explain RAG in your own words.
8.  Ask NotebookLM to critique your explanation.

## Long-Term Knowledge Management

``` text
Concept
--------
Attention
Transformers
Embeddings

Integration
-----------
How LLMs Work
How RAG Works

Projects
--------
Local RAG
AI Assistant
```

Rather than one massive notebook, create focused notebooks and connect
ideas through integration notebooks.

## Advanced Tips

-   Curate sources aggressively.
-   Ask comparison questions.
-   Challenge explanations.
-   Record your own insights.
-   Revisit notebooks after building projects.

## Recommended Ecosystem

``` text
NotebookLM
    ↓
Deep Understanding

Obsidian
    ↓
Permanent Notes & Knowledge Graph

GitHub
    ↓
Projects & Portfolio
```

**Learn → Build → Document → Share**


## My workflow

1.  Search sources via notebookLM  with a prompt like 
*Find me the best sources for learning about {}. I would prefer - Official documentation Research papers, Engineering blogs, Vendor documentation* 

****
Search the web for high-quality, current sources to help me learn and map the AI concept [[hallucination]]: practical failure mode where models produce plausible but unsupported claims.

Prioritize:
1. Recent hallucination survey papers or systematic reviews.
2. Official reliability / evaluation / safety docs from OpenAI, Anthropic, Google DeepMind, Meta, Microsoft, or similar primary sources.
3. RAG evaluation guides that discuss factuality, faithfulness, groundedness, attribution, or answer correctness.
4. Practitioner-oriented sources over theory-heavy material.
****


>> Need to think about this prompt more.
2. Create a prompt sequence to learn about the concept. For example, for RAG, I would start with a prompt like: 
*Explain RAG to me as if I am an experienced Product Manager with limited ML knowledge*
>> Based on the answer prompt sequence could be changed, but at least you need three specific prompts to start with. 
3. If answer is valuable save it as a note.
4. When you have a good understanding of the concept and a batch of notes, fire this prompts
*Review all saved notes. Identify duplicates, contradictions, unsupported claims, and areas where citations to original sources are missing*
>> this give you a good idea of notes calibration.
>> Then
*Turn these notes into a clean standalone source for a PM learning. Keep only the most useful information, remove duplicates, preserve original citations where available, and add a short “scope limits” section.*
>> This will give you a clean source to use for your own learning and for future reference.
1. You can save / copy this notes compilation and use it as a source for Studio Artifacts like Quiz/Mindmap etc
2. [Optional] Create a mindmap selecting the only note as a source.
*Create a concise mind-map outline of model evals for a Product Manager.*
1. Create a quiz selecting the only note as a source.
*Create a simple multiple-choice quiz about model evals.*
1. [Optional] Create a flashcard deck selecting the only note as a source.
*Create a flashcard deck about model evals.*
*Audience: experienced Product Manager with limited ML knowledge.*
*Goal: help me remember the most important concepts and distinctions.*

Some additional notes on notebookML workflow:
- by some reason notes generation is very slow, I've noticed given notes in progress, when i create a new note, the previous note is completed at once like it generates on trigger.
- I didn't find useful to create a report on ALL SOURCES since their context much boarder than the specific concept I'm trying to learn. I found it more useful to create a report on the notes I created for the specific concept. 
- 
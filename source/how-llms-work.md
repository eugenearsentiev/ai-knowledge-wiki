# How LLMs Work at the Architectural Level
### Tokens · Transformers · Context Windows · Temperature · Parameters · Inference

---

## TL;DR

Large Language Models (LLMs) are built on six interlocking ideas:

| Concept | What it is in one sentence |
|---|---|
| **Tokens** | Text is broken into small chunks (not words) and converted to numbers before the model ever sees it |
| **Transformers** | The architecture that lets the model understand the relationship between every chunk and every other chunk simultaneously |
| **Context window** | The maximum amount of text — measured in tokens — the model can hold in "working memory" at once |
| **Temperature** | A dial that controls how predictable vs. creative the model's output is at generation time |
| **Parameters** | The numerical weights baked into the model during training — their count is the primary measure of model size and a rough proxy for capability |
| **Inference** | The process of running a trained model on your prompt to generate an answer, one token at a time |

These concepts interact constantly. You pay per token. Your context window is measured in tokens. The transformer processes all tokens in your context window. Parameters are the fixed values the model uses to compute its answer. Temperature controls how the model chooses each next token during inference. Understanding each concept separately, then together, gives you the mental model that explains 90% of LLM behavior.

---

## 1. Tokens

### Easy — The Curious Non-Technical Person

Before a language model reads any text, something needs to translate human language into a form a computer can actually calculate with. That translator is called a **tokenizer**, and the chunks it produces are called **tokens**.

Tokens are not words. They're pieces of words — sometimes a whole word, sometimes a fragment, sometimes a punctuation mark.

Take the word "unhappy." A tokenizer might split it into `un` + `happy` — two tokens. The word "cat" might be one token. The word "uncharacteristically" might be five tokens. A space before a word often gets bundled with the word itself.

Why does this matter to you? Two reasons:

**Cost.** Every service that gives you access to a language model charges by the token. When you send a message and get a reply, you're paying for every token in both directions. Longer messages cost more.

**Limits.** There's a ceiling on how much text the model can handle at once. That ceiling — called the context window — is measured in tokens, not words or paragraphs. Knowing tokens exist helps you understand why a 10-page document might hit the limit faster than you expect.

A rough rule of thumb: 1 token ≈ 4 characters of English text, or about ¾ of a word. A 1,000-word document is roughly 1,300–1,500 tokens.

---

### Middle — The Informed Practitioner

Tokenization is the first transformation in the pipeline and it has downstream consequences that affect product design, cost modeling, and even why models fail at certain tasks.

**How it works at a system level:**

The tokenizer is a separate component, trained before the model itself. It maps every possible chunk of text to an integer ID. Modern tokenizers use an algorithm called Byte Pair Encoding (BPE), which starts with individual characters and iteratively merges the most frequent pairs — producing a vocabulary of roughly 50,000–100,000 tokens that balances coverage with efficiency.

When you call an API, your text goes through the tokenizer first, becomes a sequence of integers (e.g., `[9906, 2532, 374, 1618]`), and that integer sequence is what the model actually processes.

**Practical implications for PMs and analysts:**

- **Non-English languages are token-inefficient.** English text averages ~1 token per 4 characters. Many other languages (especially those with complex scripts) need 3–5x more tokens to represent equivalent meaning. A French document costs more to process than its English translation.

- **Code is relatively efficient.** Programming languages were designed to be terse; they tokenize well.

- **Tokens explain the "how many r's in strawberry" failure.** When asked to count letters, the model is reasoning over tokens, not characters. "strawberry" might be tokenized as `straw` + `berry` — the model never sees individual letters, so character-level reasoning is genuinely hard for it.

- **Counting tokens before deployment matters.** If you're building a feature that ingests user-provided documents, you need to know roughly how many tokens a given input generates before you know whether it fits in context, and what it costs.

Tools like the [OpenAI Tokenizer](https://platform.openai.com/tokenizer) and Anthropic's token-counting API let you measure this precisely.

---

## 2. Transformers

### Easy — The Curious Non-Technical Person

For most of AI history, language models read text the same way you'd read a book: one word at a time, left to right. The problem is that by the time you reach the end of a long sentence, the beginning is "far away" and easy to lose track of.

The **transformer**, introduced in 2017, solved this with a different approach: it looks at all the words at the same time and asks, for each word, "which other words in this text are most relevant to understanding what I mean?"

Take this sentence: *"The trophy didn't fit in the suitcase because it was too big."*

What does "it" refer to — the trophy or the suitcase? A human instantly knows it's the trophy (because the trophy was too big to fit). But this requires connecting "it" to "trophy" across five words.

The transformer's core mechanism — called **attention** — does exactly this. For every word (token), it calculates a score reflecting how much attention to pay to every other word. "It" ends up strongly attending to "trophy" and weakly attending to "suitcase." This attention pattern lets the model capture meaning across any distance in the text, not just between adjacent words.

Transformers replaced older architectures for almost all language tasks because attention is both more accurate and faster to train. GPT, Claude, Gemini — they all run on transformer architectures.

---

### Middle — The Informed Practitioner

**Self-attention as a mechanism:**

The transformer's key innovation is **self-attention**: for each token in the sequence, compute a weighted sum of all other tokens' representations, where the weights reflect relevance. This produces **contextual embeddings** — the same word gets a different vector depending on its context. "Bank" in "river bank" and "bank account" will have very different representations after attention, even though they started from the same token embedding.

This is fundamentally different from older approaches (word2vec, GloVe) that gave every word a single fixed vector regardless of context.

**Encoder vs. decoder:**

Think of a publishing house with two specialist roles: a **reader/analyst** and a **writer**.

The **reader/analyst** gets a document, reads the whole thing — front to back, back to front, jumping around freely — and builds a complete understanding of it. Ask them "is this review positive or negative?" or "who is the main subject of this article?" and they'll give you a precise answer. But ask them to *write* something new and they'll hand it back: that's not their job. They understand; they don't generate.

The **writer** works differently. They're given an opening line and continue from there, word by word. They can only see what's been written so far — they can't peek at what comes next. This constraint is actually what makes them useful for generating coherent text: each word flows naturally from everything before it.

Now add a third role: the **translator**. They work in two distinct phases. First they read the entire source document and build a complete understanding of it (the encoding phase). Only once they've fully absorbed it do they start writing the translation in the target language, word by word (the decoding phase). Two separate jobs, done in sequence.

These map directly to the three transformer architectures:

| Role | Architecture | Examples | Best for |
|---|---|---|---|
| Reader/analyst | **Encoder-only** | BERT, sentence-transformers | Understanding: classification, search, semantic similarity, embeddings |
| Writer | **Decoder-only** | GPT, Claude, Llama, Gemini | Generating: chat, completion, reasoning, code |
| Translator | **Encoder-decoder** | T5, BART, original Google Translate | Transforming: translate, summarize with a target structure |

**Why this matters for what you're building:**

The models you interact with directly — Claude, GPT-4, Gemini — are all decoder-only. They generate text token by token, conditioned on everything before.

But encoder models are quietly running in the background of many AI products. When you build a RAG pipeline and need to search a document corpus for relevant chunks, you're using an encoder model to convert text into vectors (embeddings) and find the closest matches. The "retrieve" step is an encoder; the "generate" step is a decoder. Two different models, two different jobs, working in sequence — which is exactly the encoder-decoder pattern applied across separate components rather than inside one model.

**Layers and depth:**

A transformer isn't just one attention operation — it's many stacked on top of each other. GPT-3 has 96 layers. Each layer refines the representation, starting from shallow syntactic patterns and building toward higher-level semantic and world-knowledge patterns at deeper layers. This is why larger models (more layers, larger dimensions) capture more nuanced reasoning: they have more representational capacity.

**Why this matters for product decisions:**

- Models with more layers and parameters are slower and more expensive to run — this is a direct consequence of architecture depth.
- Instruction following, multi-step reasoning, and complex synthesis improve with model scale because these require the kind of high-level representation only deep layers can produce.
- When a model "misunderstands" context, it's often because the attention pattern weighted the wrong tokens — a diagnostic frame useful when writing evaluation rubrics.

---

## 3. Context Windows

### Easy — The Curious Non-Technical Person

Imagine you're working at a whiteboard. You can write things there and refer back to them as you think — but the whiteboard has a fixed size. When it fills up, you have to erase something to make room.

A language model's **context window** is its whiteboard: the total amount of text it can hold in mind at any given moment.

This includes:
- The system instructions (if any were given)
- Everything you've written in the conversation so far
- Everything the model has replied with
- Any documents you pasted in

When a conversation exceeds the context window, the model no longer has access to the parts that got pushed out. It's not that it "forgets" in a human sense — it literally cannot see that text anymore.

Why does size matter? A small context window (say, 8,000 tokens — about 20 pages of text) means the model loses the thread on long research sessions or large documents. A large context window (200,000 tokens — about 500 pages) means you can paste in a full book, a year of emails, or an entire codebase.

Most modern models have large context windows, but bigger isn't always better — we'll see why in the middle section.

---

### Middle — The Informed Practitioner

**What the context window contains:**

The context window holds the entire "working memory" of a single inference call, in token order:

1. **System prompt** — the base instructions, persona, and constraints you set
2. **Conversation history** — every prior turn (user + assistant)
3. **Injected content** — documents, search results, retrieved chunks, tool outputs
4. **Current user message**

The model has no memory outside this window. There's no persistent memory between separate API calls unless you explicitly inject it. This is why RAG, conversation summarization, and memory modules exist — they're all engineering solutions to the context window constraint.

**Context window sizes across models (mid-2025):**

| Model | Context window |
|---|---|
| GPT-3.5 | 16K tokens |
| GPT-4o | 128K tokens |
| Claude 3.7 Sonnet | 200K tokens |
| Gemini 1.5 Pro | 1M tokens |
| Llama 3.1 | 128K tokens |

**The "lost in the middle" problem:**

Larger context windows don't guarantee uniform comprehension. Research consistently shows that models perform best when the critical information is near the beginning or end of the context — material buried in the middle receives systematically less attention. This is called the "lost in the middle" problem and has practical implications:

- Don't bury the most important content in the center of a large document you pass to the model
- When designing RAG pipelines, retrieved chunks placed at the very beginning or end of the prompt are more reliably used
- Evaluation test suites (needle-in-a-haystack) routinely reveal this degradation at long contexts

**Cost implications:**

Input tokens are priced per 1M tokens. A 200K-token context costs roughly 20x what an 8K-token context costs, at equal per-token pricing. For high-volume use cases, context length is a major cost driver — which is why context caching (paying once for a static system prompt rather than per-call) is economically significant.

---

## 4. Temperature

### Easy — The Curious Non-Technical Person

When a language model generates text, it doesn't just know the one right next word — it has a ranked list of all possible next words with probabilities attached. "The sky is ___" might have: "blue" (40%), "clear" (20%), "beautiful" (15%), "falling" (2%), and so on for every word in the language.

**Temperature** is a dial that changes how the model samples from this list.

- **Low temperature (close to 0):** The model almost always picks the highest-probability word. Very predictable, very consistent. If you run the same prompt ten times, you'll get near-identical responses. Good for: answering factual questions, extracting structured data, filling in forms.

- **High temperature (1.0 and above):** The model flattens the probabilities so the second, third, and more surprising options become more likely to be chosen. More varied, more creative, but also more likely to say something unexpected — including something wrong. Good for: brainstorming, writing fiction, generating diverse options.

Think of it as a creativity dial. At zero: the model is a careful, literal fact-giver. At high values: it becomes more like a freewheeling writer who takes unexpected turns.

---

### Middle — The Informed Practitioner

**Temperature as a sampling parameter:**

Temperature is applied at inference time, not during training. It's a scalar that rescales the model's output before sampling:

- **Temperature = 0:** Always pick the highest-probability token (greedy decoding). Fully deterministic.
- **Temperature = 1.0:** Sample directly from the model's learned probability distribution.
- **Temperature > 1.0:** Flatten the distribution — increases randomness beyond the model's learned preferences.

Most API defaults sit between 0.7 and 1.0.

**When to change it and why:**

| Use case | Recommended temperature | Reason |
|---|---|---|
| Fact extraction, classification | 0.0 – 0.2 | Determinism and accuracy matter; you want the same answer every time |
| Summarization | 0.2 – 0.5 | Some paraphrase variation is fine; hallucination risk increases above this |
| Instruction following, task completion | 0.3 – 0.7 | Balanced — consistent enough to be useful, varied enough to avoid repetition |
| Creative writing, brainstorming | 0.7 – 1.2 | Diversity is the goal; some incoherence is acceptable |
| Code generation | 0.0 – 0.3 | Code either works or doesn't; low temperature reduces hallucinated syntax |

**Temperature and eval design:**

When building evaluation suites, run evals at temperature 0 to maximize reproducibility. High-temperature evals have high variance between runs, making it difficult to attribute score differences to actual model/prompt changes vs. random sampling noise.

**Related parameters:**

Temperature doesn't work alone. The full sampling stack is:

- **top-k:** Consider only the k most probable tokens, ignore the rest. Prevents extreme outliers from ever being sampled.
- **top-p (nucleus sampling):** Consider the smallest set of tokens whose cumulative probability reaches p. More dynamic than top-k — if the top token has 90% probability, only that token is in the nucleus at p=0.9.
- **Temperature is applied first**, then top-k and top-p filter the rescaled distribution.

In practice: temperature shapes the distribution; top-k/top-p clip its tail.

---

## 5. Parameters and Comparing Models

### Easy — The Curious Non-Technical Person

When people say a model has "7 billion parameters" or "405 billion parameters," they're describing how much knowledge has been baked into it.

Think of parameters as the settings on an enormous mixing board — billions of tiny dials, each tuned during training by showing the model vast amounts of text. After training, those dials are locked. When you ask the model a question, it runs your input through all those fixed settings to generate a response.

**More parameters generally means:**
- The model can hold more knowledge
- It reasons better across complex, multi-step problems
- It handles nuance, ambiguity, and subtle instructions more reliably

**But bigger also means:**
- More expensive to run (more compute needed per response)
- Slower to respond
- Larger models need more powerful hardware to serve

Common sizes you'll see talked about: 7B (7 billion — fast, cheap, capable of many tasks), 70B (powerful, more expensive), and frontier models like GPT-4 or Claude 3 Opus which are rumored to be in the hundreds of billions.

A rough mental model: a 7B model is like a very knowledgeable assistant who works fast. A 70B+ model is like a domain expert who takes a bit longer but handles harder problems. The right choice depends on what you're building and what you're willing to pay.

---

### Middle — The Informed Practitioner

**What parameters actually are:**

Parameters are the numerical weights of the neural network — the values in every matrix of the transformer (Q, K, V projections, feed-forward layers, embeddings). They're set during training and fixed during inference. When you call an API, you're running your input through these fixed weights.

Parameter count is the shorthand for model size. You'll see it written as 7B, 13B, 34B, 70B, 405B — all in billions.

**Key dimensions that define a model's architecture:**

| Dimension | What it is | Example values |
|---|---|---|
| **Total parameters** | Sum of all weight values | 7B, 70B, 405B |
| **Number of layers** | Depth of the transformer stack | 32 (7B Llama) → 126 (405B Llama) |
| **Hidden dimension (d_model)** | Width of each layer's representation | 4096 → 16384 |
| **Attention heads** | Number of parallel attention mechanisms | 32 → 128 |
| **Context window** | Max token sequence length | 8K → 1M |
| **Vocabulary size** | Number of distinct tokens | ~32K – 128K |

These dimensions together determine how a model reasons and what it can represent. A deeper model (more layers) builds more abstract representations. A wider model (larger d_model) captures more nuance per layer.

**How to compare models in practice:**

Raw parameter count is a starting point, not the answer. A 7B model trained on better data with better techniques will outperform a poorly trained 13B model on many tasks. The comparison that actually matters is **benchmark performance on tasks similar to yours**.

Commonly cited benchmarks:

| Benchmark | What it tests |
|---|---|
| **MMLU** | Multi-subject knowledge across 57 academic domains |
| **HumanEval / MBPP** | Code generation — does the output pass unit tests? |
| **GSM8K / MATH** | Grade-school and competition-level math reasoning |
| **GPQA** | PhD-level expert questions in science |
| **MT-Bench / Arena Elo** | Instruction following quality, judged by humans or LLM |
| **RULER / NIAH** | Long-context retrieval and comprehension |

**The benchmark problem:** Published scores are useful but require skepticism. Models are sometimes evaluated on data that was in their training set (contamination). Benchmarks saturate — once all models score 90%+, the benchmark stops differentiating. And benchmark performance doesn't always translate to your specific use case.

**The most reliable comparison: run your own eval** on 50–100 examples from your actual use case. A model that scores 5% lower on MMLU but performs better on your domain data is the better model for your product.

**The capability vs. cost tradeoff:**

| Tier | Examples | Best for |
|---|---|---|
| Small (3–8B) | Llama 3.1 8B, Gemma 3 4B, Claude Haiku | Classification, routing, extraction, simple Q&A |
| Medium (13–34B) | Mistral 22B, Command R | Summarization, moderate reasoning, multilingual |
| Large (70B+) | Llama 3.1 70B, Claude Sonnet | Complex reasoning, synthesis, nuanced instruction following |
| Frontier | GPT-4o, Claude Opus, Gemini Pro | Research-grade tasks, ambiguous judgment, code review |

**Instruction-tuned vs. base models:**

A base model predicts the next token — it will complete your text, not answer your question. An instruction-tuned model has been further trained (via supervised fine-tuning and RLHF) to follow instructions, maintain a helpful persona, and refuse harmful requests. For product use, you almost always want an instruction-tuned model. Base models are useful for fine-tuning your own specialized model on top of.

---

## 6. Inference

### Easy — The Curious Non-Technical Person

Inference is what happens when you actually use a trained language model.

Training is the phase where the model learns its parameters from huge amounts of text. Inference is the phase after training, when those parameters are fixed and you send the model a prompt.

When you ask ChatGPT, Claude, Gemini, or another LLM a question, you are making an **inference call**.

The model is not learning a new skill from your prompt. Instead, it is using what was already learned during training to calculate the most likely next token, then the next token after that, and so on until it has produced a complete response.

A simple way to think about it:

- **Training** is like writing and editing the cookbook.
- **Inference** is like using the cookbook to make one meal.
- **Fine-tuning** is like rewriting part of the cookbook for a specific cuisine.
- **Prompting** is like giving instructions for the meal you want right now.

During inference, the model takes your prompt, breaks it into tokens, processes those tokens through the transformer, and produces a ranked list of possible next tokens. It chooses one, adds it to the conversation, then repeats the process.

This is why LLMs feel like they are "typing" one piece at a time: under the hood, they really are generating one token at a time.

---

### Middle — The Informed Practitioner

Inference is the runtime path of an LLM product. It is the thing you pay for every time a user sends a message, uploads a document, asks for a summary, or triggers an AI workflow.

A single inference request usually has two phases:

1. **Prefill** — the model reads the input prompt and builds an internal representation of the context.
2. **Decoding** — the model generates the answer one token at a time.

During prefill, the model processes the system prompt, conversation history, retrieved documents, tool results, and the user's latest message. This is where long prompts and large context windows increase cost and latency.

During decoding, the model repeatedly predicts the next token. Each generated token becomes part of the context for the next step. If the model writes a 500-token answer, it has gone through 500 next-token prediction steps.

This distinction matters for product design:

| Product concern | Why inference matters |
|---|---|
| **Latency** | Longer prompts take more time to process; longer answers take more time to generate |
| **Cost** | You pay for input tokens and output tokens |
| **Quality** | The model can only use information included in the current inference call |
| **Reliability** | Temperature, top-p, system prompts, and retrieved context all affect the output |
| **Scalability** | Serving many users means managing GPU memory, batching, rate limits, and model choice |

Inference also explains why LLM applications need surrounding systems. The model itself has no memory between API calls unless the application provides it. If you want the model to remember a user preference, search company documents, call a tool, or use fresh data, your system has to put that information into the inference request.

So in product terms:

> Inference is not just "the model answering." It is the full runtime event where your application assembles context, sends it to the model, receives generated tokens, and turns them into a user-facing result.

---

## How They All Connect

These concepts don't operate in isolation — they form a single pipeline for every inference call:

```
Your text
    ↓ tokenizer
Token IDs  (the unit of cost, context, and generation)
    ↓ embedding lookup
Token vectors
    ↓ N × transformer layers (attention over all tokens in context window)
Contextual representations
    ↓ output projection → logits
Probability distribution over next token
    ↓ temperature + top-k/top-p + sample
Next token
    ↓ append and repeat until <EOS>
Generated text
```

That full loop is inference. The trained model is fixed; the input changes from request to request. Each request gives the model a temporary working memory through the context window, and the model uses its parameters to generate a response token by token.

The **context window** determines how many tokens can participate in the transformer's attention operation at step 3. **Temperature** governs sampling at step 6. Every single token — input and output — appears on your invoice.

Understanding this pipeline lets you reason about failure modes precisely:

- Model ignores important information → attention not reaching it (context window position effect, or the information wasn't tokenized in a way the model expects)
- Output is inconsistent across runs → temperature too high; lower it or run at 0 for evals
- Costs higher than expected → audit token counts; check for unnecessarily long system prompts or full conversation history included in every call
- Model hallucinates on retrieval tasks → the retrieved chunks may be in the "lost in the middle" zone of the context; reorder them
- Model underperforms on your task despite good benchmark scores → benchmark distribution doesn't match your task; run your own eval on domain-specific examples
- Model is too slow or too expensive → switch to a smaller model; apply quantization; route only hard cases to the large model

---

*Part of the AI PM Roadmap — Phase 1: Foundations*

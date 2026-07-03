# The AI Ecosystem: A Practitioner's Map

Artificial intelligence is a broad field concerned with building systems that perform tasks normally associated with human intelligence — perceiving, reasoning, learning, and acting. In practice, most of what people mean by "AI" today sits inside a set of nested fields, and understanding that nesting is the fastest way to orient yourself.

## The nesting

**Artificial Intelligence** is the outermost field. Inside it sits **Machine Learning (ML)**, the approach of learning patterns from data rather than hand-coding rules. Inside ML sits **Deep Learning**, which uses many-layered neural networks. And the most visible slice of deep learning right now is **Generative AI**, including the **Large Language Models (LLMs)** behind tools like ChatGPT and Claude. Each layer is a subset of the one before it: every LLM is deep learning, every deep learning model is ML, and all of it is AI — but the reverse isn't true. Plenty of useful AI (and even useful ML) involves no deep learning at all.

## The major subfields

Cutting across that nesting are application-oriented subfields, each with its own problems, datasets, and techniques:

- **Natural Language Processing (NLP)** — understanding and generating human language; the home turf of LLMs.
- **Computer Vision** — interpreting images and video, from classification to object detection to segmentation.
- **Reinforcement Learning (RL)** — agents that learn by acting in an environment and receiving rewards.
- **Speech** — recognition (speech-to-text) and synthesis (text-to-speech).
- **Robotics** — perception and control for physical systems.
- **Recommender systems** — predicting what a user will want next.
- **Multimodal AI** — models that combine text, images, audio, and more in a single system.

These subfields are the top-level map. Most concepts, models, and tools you encounter will belong to one or more of them.

## The practitioner's stack

From a builder's standpoint, an AI system moves through a recognizable pipeline: **data** (collection, cleaning, labeling) feeds **model training** (choosing an architecture and fitting it), which produces a model that is then **evaluated**, **deployed**, and **monitored** in production. The discipline around the deployment-and-monitoring end is often called MLOps. A practitioner rarely touches all of this at once — but knowing the whole pipeline helps you place any specific tool or technique.

## The major players

The current landscape is shaped by a handful of organizations. **OpenAI** (GPT, ChatGPT), **Anthropic** (Claude), **Google DeepMind** (Gemini), and **Meta AI** (Llama) build many of the best-known frontier models. **Mistral** and **DeepSeek** are notable for strong open-weight models. **Hugging Face** functions as the field's shared hub for open models and datasets. Academic and research labs continue to produce the foundational ideas these companies productize.

## How to use this map

Treat this article as the index to the territory. The history of how these fields emerged, the foundations of machine learning, the neural-network architectures underneath deep learning, and the modern LLM landscape each deserve their own overview — and they connect back here. The point of the map isn't depth; it's knowing where everything lives and how the pieces relate.

# Wiki Index

Catalog of all pages, grouped by category. Updated on every ingest.

---

## Overview
- [[overview]] — Top-level AI ecosystem map; the entry point

---

## Subfields
- [[nlp]] — Natural Language Processing; home turf of LLMs; text understanding and generation
- [[computer-vision]] — Interpreting images and video; CNNs, ViT, diffusion generators
- [[reinforcement-learning]] — Agents learning from environment rewards; also powers RLHF
- [[speech]] — ASR (speech-to-text) and TTS (text-to-speech); audio-language boundary
- [[robotics]] — AI for physical systems; perception, planning, and control
- [[recommender-systems]] — Predicting what a user will want next; highest-impact ML application
- [[multimodal-ai]] — Models combining text, images, audio, video in a single system

---

## History
- [[timeline]] — AI history timeline: 1940s origins → symbolic AI → AI winters → deep learning → LLM era

---

## Concepts
- [[machine-learning]] — Learning from data; the three paradigms; where neural nets fit
- [[deep-learning]] — Many-layered neural networks; the foundation of modern AI capability
- [[generative-ai]] — Systems that produce new content (text, images, audio, code, video)
- [[llm]] — Large Language Models; transformer + pretraining + RLHF; the current frontier
- [[classical-ml]] — Stub: traditional algorithms (linear regression, SVMs, trees); details in focused KB
- [[tokenization]] — How text becomes model-readable tokens; unit of cost, limits, and generation
- [[context-window]] — Temporary working memory for an LLM call; where prompts, history, and retrieved data fit
- [[inference]] — Runtime path for a trained model: prefill context, decode output token by token
- [[sampling]] — Temperature, top-k, and top-p controls for choosing generated tokens
- [[parameters]] — Learned model weights; rough size/capacity signal but not the whole comparison
- [[embeddings]] — Vector representations used inside models and for semantic search/RAG
- [[hallucination]] — Practical LLM failure mode: fluent answers that are false, fabricated, or unsupported
- [[factuality]] — Whether an AI answer's claims are true in the world
- [[faithfulness]] — Whether an AI answer is supported by the provided prompt, context, documents, or tool results
- [[groundedness]] — Whether an AI answer is anchored in supplied evidence
- [[context-recall]] — RAG diagnostic: whether retrieval found the information needed to answer
- [[citation-mismatch]] — Failure where a cited source does not actually support the generated claim

---

## Architectures
- [[transformer]] — The dominant architecture; attention mechanism; foundation of all modern LLMs
- [[cnn]] — Convolutional Neural Networks; spatial/image data; AlexNet lineage
- [[rnn-lstm]] — Recurrent nets and LSTMs; sequence models before the Transformer era
- [[gan]] — Generative Adversarial Networks; generator vs. discriminator; now largely superseded by diffusion
- [[diffusion-models]] — Generative models via learned denoising; powers Stable Diffusion, DALL·E
- [[autoencoder]] — Compress-and-reconstruct; dimensionality reduction; component in diffusion models
- [[mlp]] — Multilayer Perceptron; fully-connected baseline; building block inside larger models

---

## Techniques
- [[prompting]] — Crafting input to steer LLM output; umbrella for prompt engineering patterns
- [[zero-shot-prompting]] — Direct prompting without examples; simplest starting pattern
- [[few-shot-prompting]] — Prompting with examples to teach format, style, or label conventions
- [[chain-of-thought-prompting]] — Reasoning/rationale prompting for multi-step analysis and tradeoffs
- [[structured-output-prompting]] — Constraining model output into JSON, tables, fields, or schemas
- [[prompt-templates]] — Reusable prompt patterns with slots for context, constraints, and output format
- [[llm-as-judge]] — Using an LLM to grade model outputs for automated evals and regression checks
- [[spec-driven-development]] — Using specs, plans, and tasks to guide AI-assisted software development
- [[ears-requirements]] — Structured natural-language requirements syntax used in SDD workflows
- [[rag]] — Retrieval-Augmented Generation; fetch documents at query time to ground answers
- [[fine-tuning]] — Further training a pretrained model on domain-specific data
- [[rlhf]] — Reinforcement Learning from Human Feedback; how base models become assistants
- [[lora]] — Low-Rank Adaptation; parameter-efficient fine-tuning; enables consumer-hardware training
- [[quantization]] — Reducing weight precision to shrink models; makes large models runnable locally
- [[agents-tool-use]] — LLMs that call external tools and take multi-step actions
- [[pretraining]] — First large-scale training phase on broad data; creates the general prior
- [[guardrails]] — System controls that constrain LLM inputs, retrieval, tool use, and outputs
- [[rag-evaluation]] — Diagnostic checks for retrieval quality, answer relevance, faithfulness, and groundedness

---

## Models
- [[gpt]] — GPT family (OpenAI); decoder-only Transformer; GPT-3 → GPT-4 → o-series
- [[claude]] — Claude family (Anthropic); Constitutional AI; Haiku/Sonnet/Opus tiers
- [[gemini]] — Gemini family (Google DeepMind); natively multimodal; 1M-token context
- [[llama]] — Llama family (Meta AI); leading open-weight LLM series; basis for community fine-tunes
- [[stable-diffusion]] — Open-weight latent diffusion model for text-to-image; Stability AI
- [[dalle]] — DALL·E (OpenAI); closed text-to-image diffusion; integrated into ChatGPT
- [[alexnet]] — AlexNet (2012); the CNN that launched the deep learning era; won ImageNet
- [[bert]] — BERT (Google, 2018); encoder-only Transformer; pre-train → fine-tune paradigm for NLP
- [[deepseek]] — DeepSeek; Chinese lab with high-performing open-weight models; efficient RL training

---

## Organizations
- [[openai]] — Creator of GPT, ChatGPT, DALL·E; led the current generative AI wave
- [[anthropic]] — Creator of Claude; safety-focused; Constitutional AI
- [[google-deepmind]] — Creator of Gemini, AlphaGo, AlphaFold; Transformer paper origin
- [[meta-ai]] — Creator of Llama; open-weight strategy; PyTorch; Yann LeCun's home
- [[mistral]] — French lab; efficient open-weight models; Mixture-of-Experts architecture
- [[hugging-face]] — The field's open hub: transformers library, model/dataset hosting, Spaces

---

## People
- [[geoffrey-hinton]] — "Godfather of Deep Learning"; AlexNet co-author; 2018 Turing Award
- [[yann-lecun]] — Pioneered CNNs (LeNet); Chief AI Scientist at Meta; 2018 Turing Award
- [[yoshua-bengio]] — Deep learning foundations; attention precursors; AI safety advocate; Turing Award
- [[rich-sutton]] — Co-founder of modern RL; co-authored the standard RL textbook; wrote The Bitter Lesson
- [[alan-turing]] — Proposed the Turing Test (1950); foundational computability theory
- [[andrej-karpathy]] — OpenAI/Tesla; influential educator; neural networks from scratch (Zero to Hero)
- [[john-mccarthy]] — Coined "Artificial Intelligence"; organized Dartmouth Workshop (1956)
- [[ilya-sutskever]] — AlexNet co-author; OpenAI co-founder; drove GPT-3/ChatGPT; founded SSI

---

## Papers
- [[attention-is-all-you-need]] — "Attention Is All You Need" (2017); introduced the Transformer
- [[bitter-lesson]] — "The Bitter Lesson" (Sutton, 2019); general methods + compute always win
- [[alexnet-imagenet]] — AlexNet/ImageNet paper (2012); launched the deep learning era

---

## Tools & Apps
- [[chatgpt]] — OpenAI's consumer chat product; GPT-4 interface; the 2022 public inflection point
- [[ollama]] — Run open-weight LLMs locally; simple CLI; wraps llama.cpp
- [[langchain]] — Python framework for LLM applications; chains, agents, RAG pipelines
- [[open-brain]] — Self-hosted persistent memory layer for AI tools; MCP-native; RAG under the hood
- [[lm-studio]] — GUI desktop app for running LLMs locally; similar scope to Ollama
- [[vibe-coding-tools]] — AI app builders and coding agents that turn natural-language intent into software
- [[github-spec-kit]] — Open-source SDD toolkit for turning feature ideas into specs, plans, tasks, and implementation
- [[kiro]] — AI development environment centered on specs, EARS-style requirements, designs, tasks, and hooks
- [[openapi]] — Machine-readable HTTP API specification; mature example of spec-first tooling

---

## Reference
- [[data-science-books]] — Curated reading list for data science and ML practitioners
- [[model-classifications]] — Practical axes for classifying AI models by family, openness, size, deployment, and use case
- [[model-evals]] — Shallow map of LLM evaluation modes: benchmarks, preference tests, automated judges, and risk audits
- [[ai-benchmarks]] — Orientation to common model benchmarks such as MMLU, HELM, and Chatbot Arena-style rankings
- [[sdd-reading-list]] — Reading map for spec-driven development, tools, practices, and 2026 research themes

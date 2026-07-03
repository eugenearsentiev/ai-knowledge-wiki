# The LLM and Generative AI Landscape

Generative AI — systems that produce new content rather than just classifying or predicting — is the most visible frontier of the field today. At its center are Large Language Models (LLMs), but the broader landscape spans text, images, audio, video, and code. This overview maps the models, the techniques, and the tools a practitioner encounters.

## What an LLM is

A Large Language Model is a transformer-based neural network trained on vast amounts of text to predict the next token (roughly, the next word-piece) in a sequence. That simple objective, scaled to enormous models and datasets, yields systems that can write, summarize, translate, reason through problems, and generate code. Training typically has two phases: **pretraining** on a broad corpus to build general capability, followed by **fine-tuning** and alignment steps to make the model helpful and safe for specific uses.

## Generative AI beyond text

The generative wave isn't limited to language. **Diffusion models** generate images from text prompts. Related approaches produce audio, music, speech, and increasingly video. Code generation has become a major application in its own right. Many frontier systems are now **multimodal**, accepting and producing combinations of text, images, and audio in a single model.

## The model families

A handful of model families anchor the landscape. **GPT** (OpenAI), **Claude** (Anthropic), **Gemini** (Google DeepMind), and **Llama** (Meta) are among the best known, alongside strong open-weight models from **Mistral** and **DeepSeek**. On the image side, **Stable Diffusion**, **DALL·E**, and **Midjourney** are widely used. A key practical distinction is **closed/proprietary** models (accessed through an API) versus **open-weight** models (downloadable and runnable yourself), and relatedly, **cloud** versus **local** deployment.

## The core techniques

Several techniques recur constantly in practice:

- **Prompting** — crafting the input to steer the model's output; the most accessible lever.
- **Retrieval-Augmented Generation (RAG)** — fetching relevant documents at query time and feeding them to the model, so answers draw on external or up-to-date knowledge.
- **Fine-tuning** — further training a base model on domain-specific data to specialize it.
- **RLHF** (Reinforcement Learning from Human Feedback) — using human preferences to align a model's behavior.
- **LoRA** and other parameter-efficient methods — adapting large models cheaply by training small add-on weights.
- **Quantization** — shrinking models so they run on smaller hardware.
- **Agents and tool use** — letting a model call external tools, take multi-step actions, and orchestrate workflows rather than just answering once.

## The tools and apps

The ecosystem around these models is large. **ChatGPT** and **Claude** are mainstream chat applications. **Ollama** and **LM Studio** let you run open models locally. **LangChain** and similar frameworks help developers build applications on top of LLMs. **Hugging Face** hosts open models, datasets, and libraries that much of the field depends on.

## Putting it together

The throughline from the rest of the backbone lands here: the transformer architecture made LLMs possible, the deep learning revolution made transformers possible, and the long history of the field set the stage. For a practitioner, the landscape breaks cleanly into three questions — *which model*, *which technique*, *which tool* — and most day-to-day work is some combination of the three.

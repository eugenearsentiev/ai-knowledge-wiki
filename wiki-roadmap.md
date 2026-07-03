# Wiki Roadmap

Roadmap of missing or underrepresented topics for the AI ecosystem wiki. Keep new pages shallow and link out when a topic wants depth.

## Highest-priority stubs

- [[evaluation]] — How model quality is measured; connects benchmarks, eval suites, human preference, and deployment risk. Read: Stanford HELM, OpenAI Evals, Anthropic evals posts.
- [[benchmarks]] — Public tests and leaderboards used to compare models, plus their failure modes. Read: LMSYS Chatbot Arena, HELM, Papers with Code, Hugging Face Open LLM Leaderboard.
- [[hallucination]] — Practical failure mode where models produce plausible but unsupported claims. Read: hallucination surveys, OpenAI/Anthropic reliability docs, RAG evaluation guides.
- [[ai-safety-alignment]] — Alignment methods, safety research, refusal behavior, and governance. Read: Constitutional AI, OpenAI alignment posts, DeepMind safety papers.
- [[mixture-of-experts]] — Sparse architecture pattern behind efficient frontier-scale models. Read: Switch Transformer, Mixtral, DeepSeek technical reports.
- [[vector-databases]] — Retrieval infrastructure used by RAG systems. Read: FAISS docs, Pinecone docs, Weaviate docs, Chroma docs.
- [[model-serving]] — Runtime systems for deploying and optimizing inference. Read: vLLM, TensorRT-LLM, llama.cpp, Hugging Face Text Generation Inference.
- [[clip]] — Vision-language representation model that connects image and text. Read: OpenAI CLIP paper and blog.
- [[alphafold]] — Scientific AI milestone for protein-structure prediction. Read: AlphaFold Nature papers and DeepMind explainer.
- [[codex]] — Coding-model lineage connecting GPT-style models to programming assistants. Read: OpenAI Codex paper/blog and GitHub Copilot materials.

## Useful medium-priority topics

- [[datasets]] — Training corpora and data pipelines behind model capability. Read: The Pile, Common Crawl, LAION, Hugging Face Datasets.
- [[leaderboards]] — How public rankings shape model perception. Read: LMSYS Arena, HELM, Open LLM Leaderboard.
- [[alphago]] — Deep RL milestone that made modern AI visible before the LLM wave. Read: AlphaGo Nature paper and DeepMind documentary.
- [[word2vec]] — Historical bridge from NLP embeddings to representation learning. Read: Mikolov et al. word2vec papers.
- [[seq2seq]] — Pre-Transformer sequence modeling pattern. Read: Sutskever et al. 2014.
- [[vision-transformer]] — Transformer architecture in computer vision. Read: An Image is Worth 16x16 Words.
- [[interpretability]] — Understanding and debugging model internals. Read: Anthropic mechanistic interpretability posts and Distill circuits work.

## Product and tool pages to consider

- [[midjourney]] — Major image-generation product; useful contrast with [[stable-diffusion]] and [[dalle]].
- [[perplexity]] — AI search product built around retrieval and answer synthesis.
- [[cursor]] — AI coding environment; fits beside [[vibe-coding-tools]], [[kiro]], and [[github-spec-kit]].
- [[claude-code]] — Agentic coding tool distinct from the [[claude]] model family.

## Suggested next ingest batch

1. [[evaluation]] + done 
2. [[benchmarks]] + done as part of [[model-evals]] and [[ai-benchmarks]] pages
3. [[hallucination]] + done
4. [[ai-safety-alignment]]
5. [[mixture-of-experts]]
6. [[vector-databases]]
7. [[model-serving]]
8. [[clip]]
9. [[alphafold]]
10. [[codex]]

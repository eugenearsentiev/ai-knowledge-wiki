---
type: architecture
tags:
  - "architecture"
  - "diffusion-models"
  - "gan"
  - "stable-diffusion"
  - "dalle"
  - "autoencoder"
  - "transformer"
  - "computer-vision"
  - "generative-ai"
---

# Diffusion Models

A generative model family that learns to reverse a gradual noising process. Training adds noise to real data step-by-step; the model learns to denoise — going from random noise back to structured data — and at inference generates new samples by starting from noise.

**Why they're powerful** — stable training (unlike [[gan|GANs]]), high-quality and diverse outputs, excellent text-conditioned generation. [[stable-diffusion|Stable Diffusion]] and [[dalle|DALL·E]] are diffusion-based.

**Latent diffusion** — most practical image generators operate in a compressed **latent space** (via an [[autoencoder|autoencoder/VAE]]) rather than pixel space, making generation much faster.

**Beyond images** — diffusion models are being applied to audio, video, 3D shapes, and protein structures.

**Architecture** — modern diffusion models use a [[transformer|Transformer]] (or U-Net + Transformer) as the denoising backbone. Text conditioning is often via CLIP embeddings.

**Links** — [[computer-vision|Computer Vision]], [[generative-ai|Generative AI]], [[stable-diffusion|Stable Diffusion]], [[dalle|DALL·E]].

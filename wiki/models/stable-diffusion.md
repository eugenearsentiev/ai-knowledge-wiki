---
type: model
tags:
  - "model"
  - "stable-diffusion"
  - "diffusion-models"
  - "autoencoder"
  - "lora"
  - "dalle"
  - "openai"
  - "computer-vision"
  - "generative-ai"
---

# Stable Diffusion

An open-weight [[diffusion-models|latent diffusion model]] for text-to-image generation, developed by Stability AI. First released August 2022. One of the most significant open-source releases in generative AI — making high-quality image generation accessible for local deployment and fine-tuning.

**How it works** — operates in a compressed latent space (via a [[autoencoder|VAE]]) rather than pixel space, using a U-Net denoising backbone conditioned on text via CLIP embeddings. Faster and less memory-intensive than pixel-space diffusion.

**Ecosystem** — a large community of fine-tuned variants, [[lora|LoRA]] adapters, and UIs (Automatic1111, ComfyUI) for local use.

**vs. closed alternatives** — [[dalle|DALL·E]] ([[openai|OpenAI]]) and Midjourney are API-only; Stable Diffusion is downloadable and runs locally with no usage fees.

**Links** — [[diffusion-models|Diffusion Models]], [[autoencoder|Autoencoder/VAE]], [[computer-vision|Computer Vision]], [[generative-ai|Generative AI]], [[lora|LoRA]].

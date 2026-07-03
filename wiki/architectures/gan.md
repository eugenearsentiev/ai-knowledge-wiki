---
type: architecture
tags:
  - "architecture"
  - "gan"
  - "diffusion-models"
  - "computer-vision"
  - "generative-ai"
---

# Generative Adversarial Networks (GANs)

Introduced by Ian Goodfellow in 2014. A GAN pits two networks against each other: a **generator** that produces realistic fake data, and a **discriminator** that tries to tell real from fake. The adversarial training drives both networks to improve, producing increasingly realistic outputs.

**Applications** — photorealistic image synthesis, style transfer, image-to-image translation, data augmentation.

**Limitations** — training instability (mode collapse, failure to converge) and difficulty of evaluation made GANs notoriously tricky in practice.

**Current status** — largely displaced for high-quality image generation by [[diffusion-models|diffusion models]], which are more stable and controllable. GANs remain in use for applications requiring speed (real-time generation) or where diffusion is impractical.

**Links** — [[computer-vision|Computer Vision]], [[generative-ai|Generative AI]], [[diffusion-models|Diffusion Models]].

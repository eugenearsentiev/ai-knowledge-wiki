---
type: architecture
tags:
  - "architecture"
  - "autoencoder"
  - "diffusion-models"
  - "transformer"
  - "deep-learning"
  - "stable-diffusion"
---

# Autoencoders

A neural network that learns to compress data into a compact **latent representation** (encoder) and then reconstruct the original from that compressed form (decoder). The bottleneck forces the network to learn the most important features.

**Uses** — dimensionality reduction (nonlinear alternative to PCA), anomaly detection (unusual inputs reconstruct poorly), pretraining components, and as building blocks in generative models.

**Variational Autoencoders (VAEs)** — an extension that learns a probabilistic latent space, enabling generation of new samples by sampling from that space.

**Role in modern systems** — the encoder/decoder pattern appears throughout: [[diffusion-models|latent diffusion models]] use a trained autoencoder (VAE); the [[transformer|Transformer]] itself has an encoder and decoder stack; many systems use autoencoders for learned compressed representations.

**Links** — [[deep-learning|Deep Learning]], [[diffusion-models|Diffusion Models]], [[stable-diffusion|Stable Diffusion]].

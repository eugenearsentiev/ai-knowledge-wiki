---
type: architecture
tags:
  - "architecture"
  - "cnn"
  - "alexnet-imagenet"
  - "deep-learning"
  - "computer-vision"
  - "transformer"
  - "yann-lecun"
---

# Convolutional Neural Networks (CNNs)

A neural network architecture designed for spatial data, especially images. CNNs use learnable filters (kernels) that slide across the input to detect local patterns — edges, textures, shapes — building increasingly abstract features in deeper layers.

**Why they work for images** — translation invariance (a filter detecting an edge works anywhere in the image) and parameter sharing (one filter reused across the whole image) make CNNs efficient and effective.

**Key moment** — **[[alexnet-imagenet|AlexNet]]** (2012) demonstrated CNNs dramatically outperform prior methods on ImageNet, launching the [[deep-learning|deep learning]] era. CNNs dominated [[computer-vision|computer vision]] through the 2010s.

**Current status** — the [[transformer|Transformer]] (Vision Transformer / ViT) now leads many vision benchmarks, but CNNs remain widely used for efficiency, edge deployment, and tasks where spatial locality is key.

**Key figures** — [[yann-lecun|Yann LeCun]] (LeNet, foundational CNN work in the 1990s).

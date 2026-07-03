# Neural Networks and Deep Learning Architectures

Neural networks are the engine behind modern AI. They're a family of machine learning models loosely inspired by the brain, and "deep learning" is simply what we call neural networks with many layers. Understanding the basic mechanics and the main architectural families is enough to place almost any modern model.

## How a neural network works

The basic unit is an artificial **neuron**, which takes several inputs, multiplies each by a learned **weight**, sums them, and passes the result through a nonlinear **activation function**. Stack neurons into **layers**, connect the layers, and you get a network. Data flows from an input layer through one or more **hidden layers** to an output layer.

Learning happens through two linked ideas. **Backpropagation** computes how much each weight contributed to the model's error, and **gradient descent** nudges every weight a small step in the direction that reduces that error. Repeat over many examples, and the network gradually fits the data. "Deep" simply means many hidden layers, which lets the network learn increasingly abstract features — edges, then shapes, then objects, for instance.

## The main architectures

Different problems call for different network structures. A handful of architectural families cover most of the landscape:

**Multilayer Perceptron (MLP)** — the classic fully-connected network. A general-purpose baseline, still used as a component inside larger models.

**Convolutional Neural Networks (CNNs)** — designed for images. They use filters that slide across the input to detect local patterns, making them efficient and effective for computer vision. AlexNet, which sparked the deep learning revolution, was a CNN.

**Recurrent Neural Networks (RNNs)** and **LSTMs** — built for sequences like text or time series, processing one element at a time while carrying a memory of what came before. LSTMs added gating to handle longer dependencies. They were the standard for language tasks before transformers largely replaced them.

**Transformers** — introduced in the 2017 paper "Attention Is All You Need," these use a mechanism called **attention** to weigh the relevance of every part of the input against every other part, all at once. This parallelism and ability to capture long-range relationships made transformers the foundation of modern LLMs and much else. This is the single most important architecture to understand today.

**Generative Adversarial Networks (GANs)** — pit a generator against a discriminator in a contest, producing realistic synthetic images and other data.

**Autoencoders** — learn to compress data into a compact representation and reconstruct it, useful for dimensionality reduction and anomaly detection.

**Diffusion models** — generate images (and other media) by learning to reverse a gradual noising process. They power most of today's leading image generators.

## How the pieces connect

Architecture choice follows the data: CNNs for spatial structure, recurrent and transformer models for sequences, diffusion and GANs for generation. The transformer's rise is the throughline of the current era — it didn't just improve language modeling, it became a general-purpose backbone showing up in vision, audio, and multimodal systems too. The next overview, on the LLM and generative AI landscape, picks up where this one leaves off.

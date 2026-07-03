# Machine Learning Foundations

Machine learning is the branch of AI where systems improve at a task by learning patterns from data, rather than following rules a programmer wrote by hand. Instead of specifying *how* to solve a problem step by step, you provide examples and let an algorithm infer the underlying pattern. Almost everything in modern AI rests on this idea.

## The three learning paradigms

ML is usually divided into three broad styles, distinguished by what kind of feedback the algorithm gets.

**Supervised learning** uses labeled examples — inputs paired with the correct outputs — and learns to predict the output for new inputs. It splits into two main tasks: **regression** (predicting a continuous number, like a house price) and **classification** (predicting a category, like spam vs. not-spam). This is the most common paradigm in practice.

**Unsupervised learning** works with unlabeled data and tries to find structure on its own. Typical tasks include **clustering** (grouping similar items) and **dimensionality reduction** (compressing data while preserving its important structure).

**Reinforcement learning** has an agent learn by interacting with an environment, taking actions and receiving rewards or penalties. Over time it learns a policy that maximizes long-term reward. It underpins game-playing systems and is increasingly used to fine-tune large models.

## Common supervised algorithms

A practitioner's toolkit of classical algorithms includes:

- **Linear regression** and **logistic regression** — simple, interpretable baselines for regression and classification.
- **Decision trees** — rule-like splits that are easy to read.
- **Random forests** and **gradient boosting** (e.g. XGBoost) — ensembles that combine many trees for strong, robust performance on tabular data.
- **Support vector machines (SVMs)** — finding the boundary that best separates classes.
- **k-nearest neighbors (k-NN)** — classifying by similarity to nearby examples.

These "classical" methods remain the right tool for many real-world problems, especially structured/tabular data where deep learning offers little advantage.

## Common unsupervised methods

- **k-means** — partitioning data into k clusters.
- **Principal Component Analysis (PCA)** — reducing dimensions while keeping the most variance.

## Core concepts every practitioner needs

Several ideas show up regardless of algorithm. **Features** are the input variables the model learns from, and **feature engineering** — choosing and transforming them — often matters more than the algorithm itself. Data is split into **training** and **test** sets so performance can be measured on examples the model hasn't seen. The central tension is **overfitting** (memorizing the training data and failing to generalize) versus **underfitting** (being too simple to capture the pattern) — often framed as the **bias-variance tradeoff**. Models are judged with **evaluation metrics** like accuracy, precision, recall, and others suited to the task.

## Where neural networks fit

Neural networks are simply one family of ML models — extremely flexible and powerful, especially for unstructured data like images, audio, and text. When networks get many layers, the field calls it deep learning, which is the foundation of today's most capable systems. But neural networks are a part of ML, not a replacement for it; a great deal of valuable work still uses the classical methods above.

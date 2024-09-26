---
title: Is knowledge distillation a scam really?
date: '2024-09-25 19:13:51'
tags:
---

## Motif

Knowledge distillation caught my attention when I first started reading machine learning papers. But recently, this topic has become more confusing after I came across [this notebook that claims knowledge distillation is a scam](https://github.com/geohot/ai-notebooks/blob/master/cifar10_distillation.ipynb) (which shows similar results to [PyTorch’s tutorial](https://pytorch.org/tutorials/beginner/knowledge_distillation_tutorial.html)) and the paper [Mamba in the Llama](https://arxiv.org/pdf/2408.15237). So, I invite you, the reader, to join me on my journey to figuring this out.

## What is Knowledge Distillation?

Knowledge distillation aims to produce a smaller student model from a larger teacher model. To achieve this, we set up an objective function where the student model tries to match the predictions of the teacher model. 

From [what I’ve learned](https://youtu.be/A5ff8hu1amM?t=274), there are two popular ways to do this:

1. **Logit Matching**: The student model directly tries to match the logits (un-normalized predictions) of the teacher model (used in models like GEMMA 2).
2. **Sequence Imitation**: The teacher model generates output sequences, and the student model learns from these sequences (effective in settings where the input is conditioned on prompts). 

Typically, the weights of the student model are initialized with those from the original (teacher) model (as seen in models like DistilBERT, Mamba in the Llama, etc.).

## Questions I Have About Distillation

- Is distillation actually effective?
- Is distillation better than training directly from the original dataset?
- Is distillation just adding extra training epochs?
- What can we omit during the distillation phase?

## My Instinct

My intuition is that distillation makes sense but shouldn’t be applied to every part of the model. Dropout suggests that models can be compressed into smaller versions. However, the real challenge seems to be how to preserve key channels while removing redundancies—without overfitting.


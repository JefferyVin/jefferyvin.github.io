---
title: Pretending I'm llm
date: 2024-11-30 22:57:43
published: 'true'
theme: xray
password: jz0218
abstract: hidden
categories:
  - 随笔
---

J: ugh
L: What's wrong?
J: Dude... I dont know anymore.. 
L: I know that you are working on Machine learning side of things last time we talked. Did you encounter some sort of bottleneck? Or perhaps something cuases you to be demotivated?
J: Yeah sorta...
L: What happend?
J: So you know I've been working on LLMs currently. For the past year or so, the meta of LLMs are revolved around transformer models. I always have some doubt about the capabilities of Transformers. But last month, Yann Lecun stated that LLMs cannot reason. I mean I agree with him, but given the training set that was given... It is hard to get "good" training data from internet because the context is usually hidden, or sometimes people will jump to conclusion without solid facts backing their conclusion. You know that sort of things. 
L: I get what you're saying. Transformers, while groundbreaking, do have limitations—especially when it comes to reasoning in a way that's close to how humans process information. A lot of what they "know" comes from statistical associations, which doesn't necessarily mean understanding or reasoning. Yann LeCun’s point about reasoning makes sense because reasoning often requires integrating multiple layers of context, performing logical deductions, or applying external knowledge dynamically, which isn’t a transformer’s forte.

J: Exactly! And when you rely on data scraped from the internet, it’s inherently messy. Misleading information, lack of proper context, contradictions... It's not the kind of structured, reasoning-focused dataset that would make a model excel at reasoning tasks.

L: That’s a real challenge. It’s almost like transformers are exceptional at pattern matching but struggle when tasked with reasoning tasks that demand true causal inference or abstract thinking. Do you think this is a limitation of the transformer architecture itself, or is it more about the way models are being trained and the data they’re exposed to?

J: Honestly, maybe a mix of both. Transformers are definitely powerful for capturing relationships and patterns in language, but they’re not inherently designed for reasoning in the way humans understand it. And the data problem just amplifies the issue.

L: Makes sense. So what’s the plan? Are you thinking of experimenting with alternative architectures or approaches, or is it more about figuring out how to better preprocess or structure training data to close the gap?

J: Ugh.. I've thought about different things. Such as adding reasoning in the training data by fact checking but I'm afraid the model needs to be able to do fact checking inherently. But if the model use the knowledge of the internet for fact checking, I'm worried that it would be vulnerable to advertisements and false, useless, outdate information. I also thought about other things such as storing information as episodic memory in the form that is not token based. What Yann Lecun suggested: Energy based model, optimization based inference, bayesian inference, System 2 stuff, Joint embedding predictive architecture also interests me but I dont know much about them.

L: You're really wrestling with some deep questions here. It's good that you're open to exploring a variety of directions—it shows you're not locked into the current "meta" of transformers. Let’s unpack these ideas a bit.

1. Fact-checking in Training or Inference:
You're right to worry about the pitfalls of relying on internet knowledge for fact-checking. The internet is a noisy place, full of contradictions and biases. Building inherent fact-checking into a model might require:

Structured Knowledge Integration: Instead of letting the model "roam" the internet, you could use curated, high-quality datasets (e.g., scientific papers, verified encyclopedias, databases).
Real-Time Validation Mechanisms: Models could cross-verify their output with external trusted sources at inference time, rather than just during training. This would allow the model to dynamically adapt to newer, more accurate information.
Reasoning as a Learned Behavior: Maybe introducing specialized modules or tasks during training that explicitly require reasoning chains (e.g., multi-hop reasoning, causal analysis).
But yes, these approaches only go so far—reasoning might require more fundamental architectural changes.

2. Episodic Memory Beyond Tokenization:
This is a fascinating direction. Token-based memory makes models heavily context-dependent, meaning they forget "past experiences" as soon as context length is exceeded. Episodic memory could mimic human-like recollection where:

Memories are stored as high-level semantic embeddings or events, not token strings.
Retrieval involves semantic similarity searches for relevant "episodes" rather than just operating within the context window.
It enables the model to retain information across sessions, adapting over time without retraining.
For this, you’d need memory architectures or external databases capable of efficiently organizing and retrieving non-tokenized, meaningful "events" or "facts."

3. Exploring LeCun's Ideas:
The concepts Yann LeCun promotes—like energy-based models (EBMs), optimization-based inference, and system 2 architectures—could open doors to better reasoning and problem-solving. Here's a quick rundown:

Energy-Based Models (EBMs): They focus on assigning low energy to correct or likely configurations and high energy to incorrect ones. They're less reliant on token-based sequences and could be trained to prioritize plausible reasoning over simple statistical correlations.
Optimization-Based Inference: Rather than generating answers in one forward pass, models could iteratively refine outputs, searching for a solution that minimizes error or maximizes consistency with given data.
Bayesian Inference: Probabilistic approaches could be useful for handling uncertainties, something transformers currently don't do well.
System 2 Thinking: Inspired by cognitive science, this approach would separate fast, intuitive "pattern-matching" (System 1) from deliberate, logical "reasoning" processes (System 2). This might involve hybrid architectures or even combining multiple specialized models.
Joint Embedding Predictive Architectures (JEPA): If I understand it correctly, JEPA emphasizes learning predictive representations in ways that integrate multimodal or multi-context data. It’s about making generalizations while grounding predictions in structured contexts.
L: These are exciting but complex directions. Maybe you don’t need to implement them all—just picking one idea to explore deeply could yield insights. Are there any specific resources, papers, or experiments you'd want to dive into first?

---
title: Streetfight Transformers Notes
date: '2024-09-27 21:26:38'
toc: true
tags:
---

# My Takeway
Example: LLama 3.1 8B
Layers (N): 32, Model Dim(D): 4096, FFN Dim: 14336, Attention Heads(NH): 32, K/V Head 8, Vocab Size(V): 128,000
Estimated Param ≈ 128,000 * 4096 + 32 * 4 * 4096 * 4096 + 32 * (4096 * 14336 * 2) ≈ 6.4 B
Miss Params that I can think of: WPE 
Overhead = 25% ig

Memory wise: 
In order to Inference it you need:
B = 1
Param + N * T * B * 2D = 8B + 32 + 128000 * B * 4096*2 ≈ 8B 
inference:
INT8 = 1 byte = 8GB
BFloat16 = 2 byte = 16 GB
TF32 = 2.375 byte = 19 GB

Train:
3 * N * 12 * D * D + N * T * B * 12 * D = 3 * 32 * 12 * 4096 * 4096 + 32 * 128000 * 1 * 12 * 4096 ≈ 220B
TF32 = 220 * 2.375 ≈ 522 GB = 8 H100s to train batch size of 1

Finetune:
B = 1
R = 64
N\*12\*D\*D+N\*2\*D\*R (Param) \+2\*N\*2\*D\*R (Adam) \+ B\*N\*T\*(D+R+D+D+D) =  32 * 12 * 4096 * 4096 + 2 * 4096 * 64 + 2 * 32 * 2 * 4096 * 64 + 1 * 32 * 128000 * (4 * 4096 + 64) ≈ 73B
TF32 ≈ 173 GB = 8 5090s(if its 24/32gb) to train batch size of 1
B = 4
2 * 12 * 4096 * 4096 + 2 * 4096 * 64 + 2 * 32 * 2 * 4096 * 64 + 4 * 32 * 128000 * (4 * 4096 + 64) = 270B ≈ 641GB ≈ 8 H100s with mixed precision maybe

maybe with mixed precision you can finetune on 8xH100s 

Ok time to earn enough money to buy 8xH100s! It's only $260,500!

<!-- more -->

# Notes on [Street Fighting Transformers](https://youtu.be/ZAO6y_oJtFA)

## What to know

- Parameters  
- Compute  
- Memory

## When to know it

- Training  
- Fine-tuning  
- Inference

## Notation

B \- batch  
D \- default hidden

Units:  
Parameters: Bytes (x2/x4)  
Compute: FLOPs (\~x2)  
Memory: Bytes (x2/x4) (Depends on mixed prec.)

For Parameters \= D\*2D,   
Training:  
Memory \= D\*2D (parameters) \+ 2\*D\*2D (Adam optimizer) \+ B\*D+B\*2D (all activations),  
Compute \= B\*D\*2D (forward) \+ 2\*B\*D\*2D (backward)

Inference:   
Memory \= D\*2D (parameters) \+ B\*2D (biggest activation),  
Compute \= B\*2D\*D

## Simple NN

Structure of D-\>2D-\>D  
Parameter \= 2\*D\*2D

### Training:

Memory \= 2\*D\*2D (param.) \+ 2\*2\*D\*2D (Adam) \+ B\*D+B\*2D+B\*D (all activations),  
Compute \= B\*2\*D\*2D (forward) \+ 2\*B\*2\*D\*2D (backward)

### Inference:

Memory \= 2\*D\*2D (param) \+ B\*2D (biggest activation),  
Compute \= B\*2\*D\*2D

### Fine-tuning training:

**LoRA (Ensemble With D-\>R-\>D Model) with R\<\<D:**  
Parameter \= 2\*D\*2D+2\*D\*R  
Memory \= 2\*D\*2D+2\*D\*R (Param.) \+ 2\*2\*D\*R (Adam) \+ B\*D+B\*2D+B\*D+B\*D+B\*R+B\*D (all activations)  
Compute \= B\*2\*D\*2D+B\*2\*D\*R (forward) \+ 2\*B\*2\*D\*R+B\*2D\*D (backward)  
Note: I think you need to add B\*2D\*D for the backward pass for this NN Because you need to do (part of) the backward pass to get derivatives from the Last part of the D-\>2D-\>D Neural Network. (I think, not 100% certain on it)

**Head based Fine-tuning (+D\*D in the back):**  
Param \+= D\*D  
Memory \= 2\*D\*2D+D\*D (param) \+ 2\*D\*D (Adam) \+ B\*D+B\*D (all activations)  
Compute \= B\*(2\*D\*2D+D\*D) (forward) \+ 2\*B\*D\*D (backward)

**Tail based Fine-tuning (+D\*D in the front):**  
Param \+= D\*D  
Memory \= D\*D+2\*D\*2D (param) \+ 2\*D\*D (Adam) \+ B\*D+B\*D+B\*2D+B\*D (all activations)  
Compute \= B\*(D\*D+2\*D\*2D) (forward) \+ 2\*B\*(D\*D+2\*D\*2D) (backward)

## Transformers

Additional Notations:  
V \- Vocab

- Input Embeddings

N \- Layers

- Feed forward  
- Attention

T \- Sequence Length

### Embedding Layer

#### Parameters

V\*D

#### Compute

Nothing (Lookup)

#### Memory

Just params / optimizer

### Attention (generating qkv and output projection)

#### Parameters

N\*(3D\*D+D\*D) (3D\*D for Generating qkv and D\*D for Output Projection)

#### Compute

Forward: B\*Param  
Backward: 2\*B\*Param

#### Memory

Train: param \+ 2\*Param \+ B\*(3D+D+D+D) (All activations)  
Inference: Param \+ B\*3D (Biggest activation)

### Attention core

softmax(QK^T\sqrt(hs))V

#### Parameters

None

#### Compute (over simplified)

B\*T\*D (Forward)

#### Memory

Changes a lot

 

### Feed-Forward Layer

#### Parameters

N\*2\*4D\*D

#### Compute

Forward: B\*(N\*2\*4D\*D)   
Backward: 2\*B\*(N\*2\*4D\*D)

#### Memory

Train: Param \+ 2\*Param \+ B\*(D+4D+D) (All activation)  
Inference: Param \+ B\*4D (Biggest Activation)

### Train/Inference 

#### Parameters

N\*2\*4D\*D \+ N\*(3D\*D+D\*D) \= N\*12\*D\*D

#### Compute

Forward: N\*T\*B\*(12\*D\*D+T\*D)  
Backward \= forward\*2

#### Memory (Rough estimate)

Train: Param \+ 2\*Param \+ N\*T\*B\*(12\*D) (Activations)  
Inference: Param \+ N\*T\*B\*2D (Attention looks back, Requires Q from current step, and K,V(2D) from T-1 previous steps also know as **KV Cache**)  
Notes: Smaller Cache (GQA) use memory of N\*T\*B\*2D/C With slightly worse attention but smaller KV Cache

### LoRA (Not certain) Fine-tuning

#### Parameters

N\*12\*D\*D+N\*2\*D\*R

#### Compute

Forward: N\*T\*B\*(12\*D\*D+T\*D+2\*D\*R)

#### Memory

N\*12\*D\*D+N\*2\*D\*R (Param) \+2\*N\*2\*D\*R (Adam) \+ B\*N\*T\*(D+R+D+D+D) (Activations, I think)

### Summary

#### Parameters

\~ V\*D \+ N\*12\*D\*D

#### Compute

Forward: N\*T\*B\*(12\*D\*D+T\*D)

#### Memory

##### Bottleneck for each stage

Inference: KV Cache (N\*T\*B\*2D)  
Training: Activation / Optimizers (3\*N\*12\*D\*D \+ N\*T\*B\*(12\*D))  
Fine-tuning: Activations (B\*N\*T\*(4D+R?)) something like that  
 

## Note

Compute \!= Speed

- Memory access dominate cost  
  - A lot of the advances that have made transformers actually faster in practice have come from smarter memory access at different stages of the computation  
- Training is parallel  / inference is serial  
  - Inference is much slower because of the serial bottleneck  
- In distributed training communication is critical  
  - Bandwidth bottleneck when the model is very big

Hardware usage is critical in modern systems

### Note to self
Mabye can make a spreadsheet for it
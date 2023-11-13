---
layout: post
title: Type Inference
date: 2023-07-1
description: an autoencoder in recovering lost variable type information
tags: ML
categories: 
giscus_comments: true
related_posts: false
# related_publications: einstein1950meaning
---

# Intro

In the variable name and type inference model, it utilizes a Transformer autoencoder. This model treats C code as a language and predicts missing types and names from stripped binaries in an LLM methodology. My role involved conducting academic research, performing experiments, and developing a prototype pipeline for input data and output predictions. Furthermore, I proposed the use of a type dictionary as a novel approach to enhance accuracy in type inference. This is based on [this](https://cmustrudel.github.io/papers/ChenDIRTY2022.pdf) paper.

- Operating System: Linux
- Developemnt Environment: Ghidra, PyTorch
- Languages: shell, python

### Treating code as a language

If we treat code as a language, we can leverage a large language model to understand its patterns and make predictions. Several research studies have shown that code exhibits properties similar to natural languages.

### Decompiler of choice

In the referenced paper, the authors conducted their research using IDA as the decompiler. While there are other decompilers available, they found that Ghidra's decompilation results were not satisfactory, which hindered the learning process and yielded poor results.

### Decompiling of struct
```c
//original code

void fun() {
// stack layout:
// [xxx][padding][yyyy]
char x[3];
int y;
}
```

```c
// decompiled code

void fun() {
// stack layout:
// [xxxx][yyyy]
char x[4];
int y;
}
```

### Other research

Another research paper suggests that the limitations of Ghidra can be overcome with a straightforward workaround. They claim that using Ghidra as a decompilation tool can also yield similar results.

### The work
I used Ghidra since it is open-source, and I am more familiar with it.
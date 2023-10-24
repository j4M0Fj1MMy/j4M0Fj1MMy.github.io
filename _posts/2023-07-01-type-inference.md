---
layout: post
title: Type Inference
date: 2023-07-15
description: a autoencoder approach in recovering lost variable type information
tags: binary
categories: sample-posts
giscus_comments: true
related_posts: false
# related_publications: einstein1950meaning
---

This is an experiment on variable type prediction base on a autoencoder model approach 

### Treating code as a language
> If we treat code as a language, then we can use large language model to model the problem and therefore make prediction base on patterns. Indeed, there are research stating that code does have the property of our languages. 

### Decompiler of choice
> The author of the original paper was doing their research with IDA. While other decopmilers are also possible, they found that Ghidra is not very good at the decompilation, which confuese the learning process and made poor results. 

### Other research
> Another paper points out that the problem of Ghidra can be solved with an stright-forward workaround. And they claimed that using Ghidra as a decompilation tool also provides similar result.
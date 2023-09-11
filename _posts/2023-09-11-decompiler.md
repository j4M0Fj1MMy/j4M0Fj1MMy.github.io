---
layout: post
title: Decompiler
date: 2023-09-11 22:39:00-0400
description: some errors I encountered during the development stage
tags: decompiler
categories: sample-posts
giscus_comments: true
related_posts: false
related_publications: einstein1950meaning
---
# A no go-to decompilation of llvm IR

#### AST generation


#### llvm faulty metadata generation
missing metadata results failing checking conditions 

#### different bit length of interger literal, (128bit vs 64 bits)
Decompiler attempted to upcast a long long into 128 bit, and clang doesn't support it...

#### Invalid z3 operation
some undefined operation are generated in the binary lifting stage

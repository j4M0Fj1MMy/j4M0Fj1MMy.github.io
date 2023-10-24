---
layout: post
title: Decompiler
date: 2023-09-04
description: binary -> llvm -> C
tags: binary
categories: sample-posts
giscus_comments: true
related_posts: false
# related_publications: einstein1950meaning
---

# A no go-to decompilation of llvm IR
>First, the binary was passed to our lab's binary lifter. This produces simplified llvm intermediate representation. To enhance the reverse engineering process, we want to link(decompile) the llvm to C so that we understand the behaviour of the program faster. Even though the decompilation is inaccuarate at some point, we want to still be able to go back and look at the exact accurate llvm. 

#### AST generation
>With the clang and llvm API, the AST of the llvm is loaded. All simplification processes will be done on this AST.

### Optimization
> Many code simplification techiniques can be applied to make the decompiled code simplier to read. For example, dead code elimination, eliminate equivalent if-else condition, etc...

### Severel problems encountered
#### llvm metadata 
>missing metadata will result in failing checking conditions and crashing the program. So make sure the llvm metadata is provided and accurate. 

#### different bit length of interger literal, (128bit vs 64 bits)
> Decompiler attempted to upcast a long long into 128 bit, and clang doesn't support it...

#### Invalid z3 operation
> some undefined operation are generated in the binary lifting stage

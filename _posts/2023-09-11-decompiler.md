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

# Decompilation of LLVM IR to C

## Introduction
In our reverse engineering lab, we utilize a binary lifter to produce simplified LLVM intermediate representation (IR) from the binary files. This IR serves as a crucial step in understanding the behavior of the program. To enhance the reverse engineering process, we aim to link (decompile) the LLVM IR to C code, allowing us to grasp the program's functionality more quickly. Although the decompilation process may introduce inaccuracies, it is essential to have the ability to refer back to the precise and accurate LLVM IR representation.

## AST Generation
To achieve the decompilation of LLVM IR to C, we leverage the Clang and LLVM APIs to load the Abstract Syntax Tree (AST) of the LLVM IR. It will then be transformed to the Clang AST. All subsequent simplification processes and transformations will be performed on the Clang AST.

## Optimization
During the decompilation process, several code simplification techniques are applied to enhance the readability of the decompiled code. These techniques include dead code elimination, elimination of equivalent if-else conditions, and various other optimizations that make the decompiled code more concise and understandable.

## Challenges Encountered
Throughout the decompilation process, we faced several challenges that required careful consideration and problem-solving. The following are some of the notable challenges we encountered:

### Refinement of the condition inside if and while statement takes a very long time
One specific challenge we faced involved dealing with the if condition. When such a condition is long, it is hard to simplify the whole condition at once. Decompiling nested conditions inside if statements can significantly slow down the process. We encountered cases where handling complex conditions inside if and while statements took a considerable amount of time to refine and optimize.
```C
bool x = true;
if ((!0 && x == 1) || (1 && x == 0)) printf("foo");
if ((x == 1) || (x == 0)) printf("foo");
if ((1)) printf("foo");
printf("foo");
```

## Interesting things when decompilation is too good.
When the decompilation result is too optimized, redundant code can be removed, resulting in a decompiled code that is even simpler than the original source code. This can be an interesting outcome, showcasing the power of optimization techniques employed during the decompilation process.

## Separate function decompilation
To streamline the decompilation process and eliminate unwanted results, we found it beneficial to decompile each function separately. This approach allows us to focus on individual functions, speeding up the decompilation process and reducing the impact of slow-down caused by nested conditions inside if statements.

Please note that while the decompilation process may introduce some inaccuracies, the availability of the original LLVM IR allows us to refer back to the precise representation when necessary.
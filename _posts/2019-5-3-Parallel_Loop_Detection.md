---
layout: post
title: Parallel Loop Detection
---

As I was looking into CUDA, I learned about automatic loop threading using OpenMP and OpenACC. If parallelizing a loop can be as trivial as adding a one line directive, then the hard part becomes identifying truly parallel loops. I thought it would be interesting to explore how many parallel loops I could find using mostly dynamic instrumentation.

![alt text](/assets/projects/Instrumentation.jpg)

<!--more-->

Dynamic instrumentation logs all the program's memory accesses executed as a program runs. I used Intel's Pin tool to get all the memory accesses at each assembly instruction. We can analyze the accesses of iterations of for loops to determine if the iterations are independent. If so, the loop is parallel. Unfortunately, even simple Hello world programs run thousands of memory accesses, so some static analysis to filter out unrelated memory accesses can be useful.

![alt text](/assets/projects/AST_Example.jpg)


The static analysis, generated with clang, is used to modify the code so that we can get extra information about the program to filter out memory accesses that do not relate to loops. I am still having some trouble with for loops that allocate local variables within the scope of the loop. Compiler reordering of these locals makes detecting them hard. But I've been able to detect almost all loops that operate on vector and array data.
 

*Code for this project can be found **[here](https://github.com/sshafeez/CUDAfy/)**.*


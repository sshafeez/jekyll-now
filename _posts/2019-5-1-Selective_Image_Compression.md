---
layout: post
title: Selective Image Compression
---

It's very interesting to see how much matrix multiplication has been optimized using GPUs and BLAS routines. I wanted to explore the issue as a linear algebra project, but I wanted to explore an optimization that actually considers the data in a matrix and compresses parts of it to speed up matrix multiplications with that matrix.

![alt text](/assets/projects/CompressedArch.png)

<!--more-->

Our algorithm attempts to represent an n-dimension row or column vector in a matrix with a projection onto a subspace of less than n dimensions. The fewer dimensions, the faster the matrix multiplication but also the more the distortion. Here a 3D vector is being projected onto a  2D subspace M. The algorithm tries to pick a better subspace that would be closer to the original vector.

![alt text](/assets/projects/projectionOntoPlane.png)



The algorithm minimizes the distortion by building up a subspace for each vector in a way that minimizes error. The result of this is that parts of the image are untouched, while others are compressed. Compared to a known method like SVD compression, you can see that the way the spread of distortion is more discrete.

![alt text](/assets/projects/CompressedM.png) 

To see our algorithm, you can check out the cache() method in matrix.h, our custom matrix class. The code can be found **[here](https://github.com/sshafeez/HeavyMat)**. 
You can also checkout our poster for this project which compares it to SVD and Strassen algorithms.


*Click for full-size.*
[![alt text](/assets/projects/HeavyMatPoster.png "Click For Full-Size")](https://raw.githubusercontent.com/sshafeez/sshafeez.github.io/master/assets/projects/HeavyMatPoster.png)  

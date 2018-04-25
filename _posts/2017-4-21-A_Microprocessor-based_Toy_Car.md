---
layout: post
title: Microprocessor-based Toy Car
---

As part of our first year design class, we designed and built a prototype for a toy car that can follow a custom track drawn by the user.
Our proposed concept for the final product also featured special effect stickers that add more variety to gameplay.
![alt text](/assets/projects/concept.jpg)
![alt text](/assets/projects/prototype.jpg)

The algorithm operating on the data from the camera feed is quite simple and is implemented in assembly on the Altera FPGA, which is running a very reduced instruction set processor design. This a rough approximation of what the camera frame sees.
![alt text](/assets/projects/algorithm.jpg)

The car is battery powered and uses an Hbridge to drive the brushed DC motors. 

In our demos we chose to have red correspond to slow, green to fast, and blue to medium speeds.
An example of turning can be seen with a direct feed from the camera on the monitor.

---
layout: post
title: 2-Factor Authentication Lock
---

While working on my earlier Security Camera, I found it a pain to configure any sort of onboard facial recognition. Just compiling OpenCV took 13 hours on a Pi ZeroW. Thus, I decided to explore the AWS infrastructure and their AWS rekognition tool. Instead of upgrading my previous camera, I opted to create a smart door lock that requires both RFID authentication and facial recognition to enter.


*Click for full-size.*
[![alt text](/assets/projects/workflow.jpg "Click For Full-Size")](https://raw.githubusercontent.com/sshafeez/sshafeez.github.io/master/assets/projects/workflow.jpg)


The largest and most enjoyable part of this project was orchestrating and connecting all the different components. This graph gives a clean view of how the system is composed of the following components:

* Hardware:
⋅⋅⋅Raspberry Pi: Wifi enabled controller for the remanining hardware.
⋅⋅⋅RFID Reader: Standard chip reader interfaced with SPI.
⋅⋅⋅Camera: A raspi specific camera (I was having responsiveness issues with a usb camera).
⋅⋅⋅Relay & Solenoid Lock: a simple solenoid that needs its own power supply to lock the door.
* Software:
⋅⋅⋅AWS Lambda: A serverless way to execute and trigger functions and handlers.
⋅⋅⋅AWS S3: Storage bucket for the photos that can be accessed from the lambda handler and raspi.
⋅⋅⋅AWS IOT: Allows communicating with ther raspi with MQTT protocol.
⋅⋅⋅AWS DynamoDB: A NoSQL database that logs all accesses and users.
⋅⋅⋅Facial Recognition: Executed using AWS Rekognition.


*Code for this project can be found **[here](https://github.com/sshafeez/doorLock)**.*

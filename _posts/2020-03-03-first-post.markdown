---
layout: post
title:  "Welcome to my blog"
date:   2020-03-04 17:32:56 +0100
categories: eda 
tags: introduction ai ml eda pytorch
comments: true
---

My keen interest in hardware technologies, coupled with my background in computer science, has driven me to pursue research in the direction of design automation algorithms and tools for architectures, for a variety of technologies. Recently, I am learning about the state-of-the-art in Deep Neural Networks~(NN) and understanding the NN strutures ([Alexnet](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf){:target="_blank"}, [Resnet](https://arxiv.org/abs/1512.03385){:target="_blank"}, etc). 

In parallel, I have started using [PyTorch](https://pytorch.org/) for implementation of DNNs. For the purpose of designing efficient NN accelerators, the first step is to find a way to extract an exact description of the NN graph. I found out the possiblity of finding the execution traces of the defined NNs using [Torchscript](https://pytorch.org/docs/stable/jit.html#mixing-tracing-and-scripting) and then parsing them into a directed graph. However, this is almost an hack! A better alternative was to look at the Open Neural Network Exchange ([ONNX](https://onnx.ai/)) format for NNs. Each ONNX model is self contained and can be accessed as a [ProtoBuf](#proto) object. PyTorch and most other deep NN frameworks allows models to be directly written to ONNX format, which makes it a common representation to be used for the process of design automation of NN accelerators. 

In the upcoming blogs, expect more details of design automation process for NN accelerators to be unveiled. 




### References 
* [ImageNet Classification with Deep ConvolutionalNeural Networks](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf){:target="_blank"}
* [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385){:target="_blank"}
* [Introduction to protocol buffers](https://developers.google.com/protocol-buffers/docs/overview){:target="_blank"}
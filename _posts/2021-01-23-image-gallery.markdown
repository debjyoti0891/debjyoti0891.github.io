---
layout: post
title:  "Just Me"
date:   2021-01-23 17:32:56 +0100
categories: eda 
tags: introduction ai ml eda pytorch
comments: true


someid:
  - aspect: "1"
    url: "me1.jpg"
    image_path: "me1.jpg"
    alt: "Close up of a butterfly"
  - aspect: "0.75"
    url: "me2.jpg"
    image_path: "me2.jpg"
    alt: "Reflection of skyscrapers in water"
    end_row: "true"
  - aspect: "1"
    url: "me1.jpg"
    image_path: "me1.jpg"
    alt: "Close up of a butterfly"
  - aspect: "0.75"
    url: "me2.jpg"
    image_path: "me2.jpg"
    alt: "Reflection of skyscrapers in water"
  - aspect: "1.78"
    url: "me3.jpg"
    image_path: "me3.jpg"
    alt: "Reflection of skyscrapers in water"
    end_row: "true"

---

{% include image-gallery.html folder="/assets/justme/me" thumbfolder="/assets/justme/thumb/" %}
  
{% include flex-gallery.html id="someid" caption="A cool caption" folder="/assets/justme/" thumbfolder="/assets/justme/thumb/" height="200px" %}

### References 
* [ImageNet Classification with Deep ConvolutionalNeural Networks](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf){:target="_blank"}
* [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385){:target="_blank"}
* [Introduction to protocol buffers](https://developers.google.com/protocol-buffers/docs/overview){:target="_blank"}
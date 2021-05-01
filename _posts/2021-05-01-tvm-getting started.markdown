---
layout: post
title:  "Code Generation with TVM"
date:   2021-05-01 00:32:56 +0100
categories: machine learning TVM 
tags: ai ml "neural network" tvm compiler
comments: true
---
[Apache TVM](https://tvm.apache.org/) is yet another compiler framework ([ONNC](https://github.com/ONNC/onnc), [MLIR](https://mlir.llvm.org/), etc.) for machine learning workloads targeted at supporting variety of hardware backends. It supports "Just in Time compilation" for the supported backends. It represents the workloads using "Relay" program, which 
can be then lowered to "[TVM IR](https://tvm.apache.org/docs/api/python/ir.html#tvm.ir.Attrs.list_field_info)" and scheduled for execution.

I started to look at the [tutorial](https://tvm.apache.org/2020/07/15/how-to-bring-your-own-codegen-to-tvm) for code generation using [DNNL](https://github.com/oneapi-src/oneDNN). The tutorial provides a relatively comprehensive guide towards 
TVM with a custom code generator, which emits JSON for certain Relay operators marked for the specific code generation backend (in this case "dnnl").  

By simply enabling the DNNL codegen in the config.cmake and compiling tvm, it is possible to generate the json from a model using the following piece of code. 
```
mod = relay.transform.AnnotateTarget(["dnnl"])(mod)
mod = relay.transform.MergeCompilerRegions()(mod)
mod = relay.transform.PartitionGraph()(mod)
graph_json, lib, params = relay.build(mod, target='llvm')
print('Graph json:', graph_json)
```
In the first step, the operators supported by the backend are annotated, which are then merged. The relay graph is partitioned and using the "build" step, the code is generated. For the operators which are not supported by the code generator, these would be executed in TVM. The generated lib includes the host module and the execution modules for the part that cannot be offloaded to the custom backend accelerator. The host module will invoke the accelerator module in runtime when it executes a graph node that is annotated for the accelerator. Currently, TVM does not support ahead of time compilation, which would allow generation of executable at compile time itself, which made TVM unsuitable for my current work. 

In summary, the framework has a lot of features for optimizing machine learning workloads without a lot of effort. However, it might be a bit complex to get started off with the documentation fragmented over a variety of pages. A relatively good order to look at the tutorials in my opinion is listed below. 

### References 
+ **Good tutorial**: This tutorial provides the quickest way to understand the primitives of a relay program. [[Link]](http://tvm.d2l.ai/chapter_getting_started/vector_add.html)
+ **TVM + Cuda** : A jupyter notebook that shows how to use CUDA as a backend. [[Link]](https://github.com/andersy005/tvm-in-action/blob/master/tvm-tutorials/getting-started.ipynb)
+ **Beginner guide** : This is a good starting point to understand the TVM code base structure. [[Link]](https://tvm.apache.org/docs/dev/codebase_walkthrough.html)
+ **Good code gen tutorial** : The tutorial provides a relatively comprehensive guide towards 
TVM with a custom code generator, which emits codes for certain Relay operators marked for the specific code generation backend.  [[Link]](https://tvm.apache.org/2020/07/15/how-to-bring-your-own-codegen-to-tvm)
+ **Available relay passes**: A number of built-in passes are already provided to optimize the relay graph. However, the passes might emit errors if the input relay graph has custom operators. [[Link]](https://tvm.apache.org/docs/api/python/relay/transform.html)










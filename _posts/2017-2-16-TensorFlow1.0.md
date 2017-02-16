---
layout: post
title: TensorFlow 1.0
categories: [blog ]
description:
comments: true
published: true
header-img: "img/18.jpg"
tags:
	- Deep Learning
	- TensorFlow
---

Keynote (TensorFlow Dev Summit 2017)



<div class="aspect-ratio">

<iframe width="560" height="315" src="https://www.youtube.com/embed/4n1AHvDvVvw" frameborder="0" allowfullscreen></iframe>

</div>



今天，在山景城召开了第一届年度 TensorFlow 开发者大会（TensorFlow Developer Summit），本次盛会也已经在 YouTube 上开启了直播。在本次大会上，谷歌也正式宣布发布 TensorFlow 1.0 正式版。



TensorFlow 1.0 仍有一些值得我们关注的亮点（以下内容来自谷歌开发者博客）：

- 速度更快：TensorFlow 1.0 快得让人难以置信！XLA 更为未来进一步的性能提升奠定了基础，而且 [http://tensorflow.org**](https://link.zhihu.com/?target=http%3A//tensorflow.org) 上现在也已经包含了帮助指导你调整你的模型以使其达到最大速度的技巧和诀窍。我们将会很快发布几种流行的模型的新实现，以表明我们可以如何充分利用 TensorFlow 1.0——包括在 8 个 GPU 上给 Inception v3 带来的 7.3 倍的速度提升和在 64 个 GPU 上为分布式 Inception v3 训练所带来的 58 倍速度提升！
- 灵活性更高：TensorFlow 1.0 引入了一个高层面的 API，带有 tf.layers、tf.metrics 和 tf.losses 模块。我们还宣布包含进了一个新的 tf.keras 模块，提供了与另一个流行的高级神经网络库 Keras 的完全兼容。
- 比以往任何时候都更适合生产：TensorFlow 1.0 保证了 Python API 的稳定性，使得你可以在无需担忧破坏你现有代码的情况下更容易地获取新功能。



TensorFlow 1.0 的其它亮点：

- Python API 已改为更类似于 NumPy 的样子。为了应用这种和其它的为了支持 API 稳定性所做的后端兼容修改，请参考我们好用的移植指南（[https://tensorflow.org/install/migration**](https://link.zhihu.com/?target=https%3A//tensorflow.org/install/migration)）和转换脚本（[https://github.com/tensorflow/tensorflow/tree/r1.0/tensorflow/tools/compatibility**](https://link.zhihu.com/?target=https%3A//github.com/tensorflow/tensorflow/tree/r1.0/tensorflow/tools/compatibility)）
- 支持 Java 和 Go 的实验性 API
- 在集成了 skflow 和 TF Slim 后从 tf.contrib.learn 带来的高级 API 模块：tf.layers、tf.metrics 和 tf.losses
- XLA 的实验性发布，这是一个用于 TensorFlow 图的特定领域的编译器，其面向 CPU 和 GPU。XLA 正在快速进化——在未来的版本中有望见证更多改进
- 引入 TensorFlow Debugger (tfdbg)，这是一个用于调试实时 TensorFlow 程序的接口和 API。
- 新的关于目标检测和定位、基于相机的图像风格化的 Android 演示
- 安装提升：加入 Python 3 docker images，TensorFlow pip 包现在已兼容 PyPI。这意味着现在可以通过简单的调用 pip install tensorflow 来实现安装。



附上Github地址：[https://github.com/tensorflow/tensorflow/releases/tag/v1.0.0](https://link.zhihu.com/?target=https%3A//github.com/tensorflow/tensorflow/releases/tag/v1.0.0)





<style>

.aspect-ratio {
  position: relative;
  width: 100%;
  height: 0;
  padding-bottom: 56%;
}

.aspect-ratio iframe {
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
}
</style>




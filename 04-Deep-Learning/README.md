# 深度学习
## 参考
* [Mastering TensorFlow 1.x  
  --Advanced machine learning and deep learning concepts using TensorFlow 1.x and Keras](https://e.jd.com/30402029.html)
* [Tensorflow环境搭建](https://www.2cto.com/kf/201612/580957.html)
* anaconda(一个开源的Python发行版本)

## 模型演进
* LeNet5的输入图像为32×32的灰度值图像，后面有3个卷积层，1个全连接层和1个高斯连接层

* AlexNet包含了6亿3000万个连接，6000万个参数和65万个神经元，拥有5个卷积层，其中3个卷积层后面连接了最大池化层，最后还有3个全连接层。

* VGGNet是牛津大学计算机视觉组（Visual?Geometry?Group）和Google?DeepMind公司的研究员一起研发的的深度卷积神经网络。VGGNet探索了卷积神经网络的深度与其性能之间的关系，通过反复堆叠3*3的小型卷积核和2*2的最大池化层，VGGNet成功地构筑了16~19层深的卷积神经网络

* Inception V1有22层深，比AlexNet的8层或者VGGNet的19层还要更深。但其计算量只有15亿次浮点运算，同时只有500万的参数量，仅为AlexNet参数量（6000万）的1/12，却可以达到远胜于AlexNet的准确率，可以说是非常优秀并且非常实用的模型
  >Inception V3有46层  
  >>The Inception v3 model takes weeks to train on a monster computer with 8 Tesla K40 GPUs and probably costing $30,000 so it is impossible to train it on an ordinary PC.  
  >>The Inception v3 model has nearly 25 million parameters and uses 5 billion multiply-add operations for classifying a single image. On a modern PC without a GPU this can be done in a fraction of a second per image.


* ResNet（Residual Neural Network）由微软研究院的Kaiming He等4名华人提出，通过使用Residual Unit成功训练152层深的神经网络，在ILSVRC 2015比赛中获得了冠军，取得3.57%的top-5错误率，同时参数量却比VGGNet低，效果非常突出。

## [ImageNet](www.image-net.org)
* ImageNet is an image database organized according to the WordNet hierarchy (currently only the nouns), in which each node of the hierarchy is depicted by hundreds and thousands of images. Currently we have an average of over five hundred images per node. We hope ImageNet will become a useful resource for researchers, educators, students and all of you who share our passion for pictures.
* The ImageNet has about 100K synsets and on average, about 1,000 human-annotated images for each synset. ImageNet only stores the references to the images while the images are stored in their original locations on the internet. In deep learning papers, the ImageNet-1K refers to the dataset released as part of ImageNet's Large Scale Visual Recongnition Challenge(ILSVRC) to classify the dataset into 1,000 categories

## CUDA
* 显卡厂商NVIDIA推出的运算平台CUDA(Compute Unified Device Architecture)，是一种通用的并行计算架构，该架构使GPU能够解决复杂的计算问题，它包含了CUDA指令集以及GPU内部的并行计算引擎。提供了硬件的直接访问接口，而不必像传统方式一样必须依赖图形API接口来实现GPU的访问，从而给大规模的数据计算应用提供了一种比CPU更加强大的计算能力。程序开发人员通过C语言，利用CUDA的指令接口，就可以编写CUDA架构的程序。

## CuDNN
* CuDNN的全称是CUDA Deep Neural Network library，CuDNN是专门针对深度学习框架设计的一套GPU计算加速方案，最新版本的CuDNN提供了对深度神经网络中的向前向后的卷积，池化，以及RNN的性能优化。目前大部分深度学习框架都支持CuDNN。

* 目前包括TensorFlow在内的大部分深度学习框架，都支持CUDA。所以，为了让我们的深度神经网络的程序在TensorFlow上跑的更加好，推荐配置至少一块支持CUDA和CuDNN的NVIDIA的显卡
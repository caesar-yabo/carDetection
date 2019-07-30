# 模型小型化总结

巨大的模型只能在有限的平台下使用，根本无法移植到移动端和嵌入式芯片当中。就算想通过网络传输，但较高的带宽占用也让很多用户望而生畏。另一方面，大尺寸的模型也对设备功耗和运行速度带来了巨大的挑战。因此这样的模型距离实用还有一段距离。

在这样的情形下，模型小型化与加速成了亟待解决的问题。其实早期就有学者提出了一系列CNN模型压缩方法，包括权值剪值（prunning）和矩阵SVD分解等，但压缩率和效率还远不能令人满意。

近年来，关于模型小型化的算法从压缩角度上可以大致分为两类：从模型权重数值角度压缩和从网络架构角度压缩。另一方面，从兼顾计算速度方面，又可以划分为：仅压缩尺寸和压缩尺寸的同时提升速度。

mobilenetv1存在的问题：https://cloud.tencent.com/developer/article/1005738













# darknet issuses

## detection small object from big images #1535

https://github.com/pjreddie/darknet/issues/1535

## Training YOLO on high resolution images  1700

Q:I want to use YOLO v3 to detect small objects (drones) in high resolution images of about 4K, the drones are about 30X30 pixels.

I noticed that darknet cfg file has image width and height, if I change them to 4k and start the train process then I immediately get an error (when the network configuration is loaded):
./src/cuda.c:36: check_error: Assertion `0' failed

If I use the default values of height = 416 and width = 416 , then I think that the image will be resized to those values before the first layer and a lot of details will be lost.

Is it possible to train YOLO with high resolution?



A:This a very challenging task. It's nearly impossible to detect such small objects with a regular network. I would divide each pictures into 4 different pictures and use them in training that way. This way you will have 4 times the dataset also. Otherwise its really difficult for yolo to detect such small objects in that huge image. If each photo has a size of 4096x2160, new photos will be 1024x540. So you can create a 1024x544(width and height should be divisible by 32) input sized neural network which will suit you best. If you want to detect small objects even better, you can use yolov3-spp.



## how to train

https://github.com/AlexeyAB/darknet#how-to-improve-object-detection

https://github.com/AlexeyAB/darknet#how-to-train-to-detect-your-custom-objects



## can yolov3 detect tiny objects #1644

Q:I've got a question in the term of tiny objects.
Can yolov3 detect small objects?? I studied some articles in this regard but I'm not sure whether it works for small objects less than 30*30 pixels or not??? if it can how should I change parameters for anchor box and aspect ratios to implement this????????
thanks



A:Of course it is possible.
Change the anchor box to a smaller size and detect it after learning. Changing only the anchor box for a network that has already been learned may not work well.

The input resolution of the neural network should be such that the size of the object is at least 10px when resized.

For example, if you want to detect objects of 50x50 size from 1920x1080 to 1024x576, you can change the input resolution to 1024x576, and you can get good results.



## How can I counting the objects and get the result #1469

https://github.com/pjreddie/darknet/issues/1469



## What is the best way to create a tiny network for YOLO#1427

https://github.com/pjreddie/darknet/issues/1427





## 图像增强和图像数据的输入

https://github.com/pjreddie/darknet/issues/1408



## Why we need K-mean clustering for YOLO? #1404

https://github.com/pjreddie/darknet/issues/1404











# 一些疑问

- 输入图片大小改为1024*576后，与原始416**416在输出有哪些不同
- 




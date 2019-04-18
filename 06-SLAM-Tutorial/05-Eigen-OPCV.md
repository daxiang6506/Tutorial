# Eigen and Open CV

## openCV

* [OpenCV: 矩阵等对象的文件存取方式](https://blog.csdn.net/eswai/article/details/53009077)
  >FileStorage fs("test.xml", FileStorage::WRITE);
  >// "data" is the label name of (I) in test.xml
  > write(fs, "data", I);
  >fs.release();
  >
  >Mat I;
  >FileStorage fs("test.xml", FileStorage::READ);
  >read(fs["data"], I);
  >fs.release();
  
* [openCV入门教程](create()函数创建对象)
  >除了在构造函数中可以创建图像，也可以使用 Mat 类的 create()函数创建图 像。如果 create()函数指定的参数与图像之前的参数相同，则不进行实质的内存 申请操作;如果参数不同，则减少原始数据内存的索引，并重新申请内存

* [OpenCV学习笔记（五十六）——InputArray和OutputArray的那些事core](https://blog.csdn.net/yang_xian521/article/details/7755101)
  >可以用_OutputArray：：needed（）来检测输出的矩阵是否需要被计算。有时候传进去的参不是空就不需要计算

* [Create a memory continuous cv::Mat, any api could do that](http://answers.opencv.org/question/22742/create-a-memory-continuous-cvmat-any-api-could-do-that/)
  > keypoints_.convertTo(keypoints_, CV_32F);

* [图像矩阵是如何存储在内存之中的？](http://www.opencv.org.cn/opencvdoc/2.3.2/html/doc/tutorials/core/how_to_scan_images/how_to_scan_images.html#howtoscanimagesopencv)

* [checkVector()](https://docs.opencv.org/3.4/d3/d63/classcv_1_1Mat.html)

* [opencv中的reshape函数](https://blog.csdn.net/s941015n/article/details/79698627)
* [OpenCV reshape函数需要注意的细节](https://blog.csdn.net/guyuealian/article/details/80252853)
  >cv::Mat mat = cv::Mat(v).clone()


## 参考

* [Eigen库中的Map类到底是做什么的](https://blog.csdn.net/baoxiao7872/article/details/80242452)
* [SolvePnp函数详解](https://blog.csdn.net/qq_30547073/article/details/78656795)
* [罗德里格斯（Rodrigues）旋转向量与矩阵的变换](https://blog.csdn.net/wangyang20170901/article/details/78800540)
* [hconcat函数 与 vconcat函数---增加行或列](https://blog.csdn.net/mangobar/article/details/79656417)
* [bool cv::solvePnP](https://docs.opencv.org/3.0.0/d9/d0c/group__calib3d.html#ga549c2075fac14829ff4a58bc931c033d)
* [Eigen介绍及简单使用](https://blog.csdn.net/fengbingchun/article/details/47378515)
* [Column-major and row-major storage](https://eigen.tuxfamily.org/dox/group__TopicStorageOrders.html)
* [How to get in and out data from Eigen matrix](http://dovgalecs.com/blog/eigen-how-to-get-in-and-out-data-from-eigen-matrix/)
* [Convert Eigen Matrix to C array](https://stackoverflow.com/questions/8443102/convert-eigen-matrix-to-c-array)
* [Strange Eigen map behavior with zero stride](https://stackoverflow.com/questions/45142461/strange-eigen-map-behavior-with-zero-stride)
* [Eigen::Map](http://eigen.tuxfamily.org/dox/classEigen_1_1Map.html)
   >Eigen can use column-major or row-major ordering of internal data storage. By default it’s column-major, but OpenCV use row-major ordering.
* [Mapping data from Eigen to OpenCV and back](https://computer-vision-talks.com/post/mapping-eigen-to-opencv/)
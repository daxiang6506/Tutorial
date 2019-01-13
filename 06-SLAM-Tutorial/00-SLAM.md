# SLAM

## 参考

* [Perspective-n-Point](https://en.wikipedia.org/wiki/Perspective-n-Point)
* [通过降维加速opencv中的knnMatch图像匹配](https://blog.csdn.net/yhyhbo/article/details/54620178c++)
* [图像处理中，outlier和inlier分别指什么](https://blog.csdn.net/daigualu/article/details/73866250)
* [slam book](https://github.com/gaoxiang12/slambook)
* [ninja](https://www.jianshu.com/p/d118615c1943)
* [欧拉角](https://blog.csdn.net/csxiaoshui/article/details/65437633)
* [eigen](http://eigen.tuxfamily.org/index.php?title-Main_Page)
  >矩阵库
* [pangolin](https://github.com/stevenlovegrove/Pangolin)
  >OpenGL封装库
* [pangolin安装及其使用](https://blog.csdn.net/c602273091/article/details/65441315)
* [Sophus](https://github.com/strasdat/Sophus)
  >李群库
  >```bash
  > cmake .. -DCMAKE_INSTALL_PREFIX:PATH=$HOME/svslocal
  > sudo make -j4
  > sudo make install
  >```
* [PCL](http://pointclouds.org)
  >Point Cloud Library
  >提供点云转换为地图的功能
* [Ceres](https://github.com/ceres-solver/ceres-solver)
  >通用最小二乘问题求解库
* [g2o](https://github.com/RainerKuemmerle/g2o)
  >通用图优化库
* [opencv](https://opencv.org)
  >[github](https://github.com/opencv/opencv/tree/3.0.0)
  >> 3.1.0 安装报错
* [卡尔曼滤波和维纳滤波](https://blog.csdn.net/sillykog/article/details/78535767)
* [李群、李代数在计算机视觉中的应用](https://blog.csdn.net/x_r_su/article/details/52749616)

## 资源

* [meshlab](http://www.meshlab.net/)
  >ubuntu app store里有
* [DBow](https://github.com/rmsalinas/DBow3)
  >DBoW3 is an improved version of the DBow2 library, an open source C++ library for indexing and converting images into a bag-of-word representation
* [BitBucket](http://tech.it168.com/a2017/1026/3176/000003176180.shtml)
  >集成了jira工具
* [OctoMap](https://github.com/OctoMap/octomap)
  >An Efficient Probabilistic 3D Mapping Framework Based on Octrees

## Bitbucket/Stash

* 生成key

  ```bash
  ssh-keygen
  cat ~/.ssh/id_rsa.pub
  ```

* ![配置Stash](_images/Bitbucket_stash.png)

## 输入法

* [Ubuntu14.04下搜狗输入法安装](https://blog.csdn.net/u011006622/article/details/69281580)

## 安装ceres

* 安装依赖包
  >```bash
  >sudo apt-get install libgflags-dev
  >sudo apt-get install libgoogle-glog-dev
  >```
* 安装本尊
  >```bash
  >sudo mkdir build
  >cd build
  >sudo cmake ../
  >sudo make
  >make install
  >```  

## 安装g2o

* 安装依赖包
  >```bash
  >sudo apt-get install libqglviewer-dev
  >sudo apt-get install libcholmod2.1.2
  >```
* 安装本尊
  >```bash
  >sudo mkdir build
  >cd build
  >sudo cmake ../
  >sudo make
  >make install
  >```  
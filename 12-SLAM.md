## 参考
* [slum book](https://github.com/gaoxiang12/slambook)
* [virtul box 挂载文件夹](https://blog.csdn.net/a962804835/article/details/72820355)
* [CMake如何查找链接库---find_package的使用方法](https://blog.csdn.net/u011092188/article/details/61425924)
* [CMake实践》笔记二：INSTALL/CMAKE_INSTALL_PREFIX](https://blog.csdn.net/primeprime/article/details/53020147)
* [自己创建XXConfig.cmake文件](https://blog.csdn.net/historycomputer/article/details/59121420)
* [hpp](https://blog.csdn.net/davidhsing/article/details/4222227)
* [ninja](https://www.jianshu.com/p/d118615c1943)
* [欧拉角](https://blog.csdn.net/csxiaoshui/article/details/65437633)
* [eigen](http://eigen.tuxfamily.org/index.php?title-Main_Page)
  >矩阵库
* [pangolin](https://github.com/stevenlovegrove/Pangolin)
  >OpenGL封装库
* [pangolin安装及其使用](https://blog.csdn.net/c602273091/article/details/65441315)
* [C++里面ostream是干什么的](https://zhidao.baidu.com/question/584182022.html?qbl=relate_question_3&word=ostream%26%20operator)
* [Sophus](https://github.com/strasdat/Sophus)
  >李群库
  >```
  > cmake .. -DCMAKE_INSTALL_PREFIX:PATH=$HOME/svslocal
  > sudo make -j4
  > sudo make install
  >```
* [PCL](http://pointclouds.org)
  >Point Cloud Library
* [Ceres](https://github.com/ceres-solver/ceres-solver)
  >通用最小二乘问题求解库
* [g2o](https://github.com/RainerKuemmerle/g2o)
  >通用图优化库
* [opencv](https://opencv.org)
  >[github](https://github.com/opencv/opencv/tree/3.1.0)
  
## 虚拟机环境搭建
使用virtual box建立环境
* ![设置内存](_images/memory.png)
  >要设置大一点
* ![设置显存](_images/video.png)
  >如果设置小了，虚拟机屏幕分辨率不够
* ![设置共享文件夹](_images/sharefolder-settings.png)
  >```
  >在宿主机上创建文件夹
  >sudo mkdir /home/usr/repo/
  >
  >#改变宿主机权限
  >sudo chmod -R 777 /home/usr/repo/
  >
  >#虚拟机创建目录
  >sudo mkdir /mnt/xuc
  >
  >#改变目录权限
  >sudo chmod -R 777 /mnt/xuc
  >
  >#挂载宿主机目录到虚拟机目录
  >sudo mount -t vboxsf repo /mnt/xuc
  >
  >#取消挂载
  >sudo umount /mnt/xuc
  >
  >#删除目录
  >sudo rm -rf /mnt/xuc
  >```
* ![网卡设置](_images/network-adaptor.png)
  >网卡要先删除，在增加，否则不能上网
* ![网络设置](_images/network-settings.png)
## 安装ceres
* 安装依赖包
  >```
  >sudo apt-get install libgflags-dev
  >sudo apt-get install libgoogle-glog-dev
  >```
* 安装本尊
  >```
  >sudo mkdir build
  >cd build
  >sudo cmake ../
  >sudo make
  >make install
  >``` 
## 安装g2o
* 安装依赖包
  >```
  >sudo apt-get install libqglviewer-dev
  >sudo apt-get install libcholmod2.1.2
  >```
* 安装本尊
  >```
  >sudo mkdir build
  >cd build
  >sudo cmake ../
  >sudo make
  >make install
  >``` 
# Localization

## 资源

* [dukto](http://www.msec.it/blog/?page_id=11)
* [glogg](http://glogg.bonnefon.org/)

## 建立环境

* [指导书](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Manual+Page+of+Localization+Refactor+May+31th+2018&spaceKey=RRT)

* [How to download dependency repository artifacts?](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=51676609)

* [Jfrog CMD Installation & Usage](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=42537772)

* [安装opencl](https://confluence.ygomi.com:8443/display/RRT/How+to+Set+Up+OpenCL+Compilation+Environment+for+FindOpenCL.cmake+in+CMake3.5)

* [Introduce sysStar tool](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Introduce+sysStar+tool&spaceKey=RRT)

* [Install Docker in Ubuntu](https://confluence.ygomi.com:8443/display/RDC/Install+Docker+in+Ubuntu)

## 虚拟机环境（最终环境没有建好，algorithm_common编译不过，可以通过jfog拉编好的库来规避）

* 安装库
  >```bash
  >sudo apt-get install libusb-1.0-0-dev
  >sudo apt-get install libudev-dev
  >sudo apt-get install libpcap-dev
  >```
* 编译core/common出错
  >```bash
  >#解决办法：
  >cp rdb-tools/core/common/thirdParty/eigen/cmake/FindEigen3.cmake  /usr/local/share/cmake-3.5/Modules/
  >```
* 解决db版本问题
  >```bash
  >#拷贝这两个文件到指定目录下（标哥提供，适配old db版本）
  >SectionMapDef.h
  >SnippetDef.h
  >core/algorithm_common/dist/x64/include
  >#然后重新编译（要用到dist下的include文件）
  >core/algorithm_vehicle_localization

## docker环境

* 命令

  ```bash
  docker run -it --name master-build -v "${PWD}":/data -w /data dockerhub.ygomi.com/rdb:latest  
  docker run --rm -it -p 8888:8888 -v $(pwd):/notebooks daxiang6506/localization:1.8.0-bokeh   
  ```

* 解决依赖问题
  >```bash
  ># 需要重新编译data-receiver
  >git clone ssh://git@stash.ygomi.com:7999/as/data-receiver.git
  ># 编译data-receiver需要rdb-device-base-rules（由标哥提供）
  >framework/device/rdb-device-base-rules
  >```
* 解决db版本问题
  >```bash
  >#拷贝这两个文件到指定目录下（标哥提供，适配old db版本）
  >SectionMapDef.h
  >SnippetDef.h
  >core/algorithm_common/dist/x64/include
  >#然后重新编译（要用到dist下的include文件）
  >core/algorithm_vehicle_localization

## C++

* [Eigen库数据结构内存对齐问题](https://blog.csdn.net/rs_huangzs/article/details/50574141)
* [ROS2入门教程-基本概念](https://www.ncnynl.com/archives/201801/2251.html)
* [ROS入门教程-1.1.10 创建ROS消息和ROS服务](https://www.ncnynl.com/archives/201608/508.html)
* [特征检测器 FeatureDetector](https://www.cnblogs.com/tianyalu/p/5468010.html)
* [Opencv的KeyPoint和DMatch数据结构](https://www.cnblogs.com/TransTown/p/7396996.html)
* [[OpenCV]DMatch类和KeyPoints类：特征点匹配](http://www.mamicode.com/info-detail-2159374.html)
* [KeyPoint Matching 优化方式](https://blog.csdn.net/yangtrees/article/details/19928191)
* [eigen与opencv矩阵转换](https://blog.csdn.net/piaoxuezhong/article/details/79110421)
* [Eigen库数据结构内存对齐问题](https://blog.csdn.net/rs_huangzs/article/details/50574141)
* [Python——cmd调用（os.system阻塞处理）](https://www.cnblogs.com/MrRead/p/7832786.html)
* [Python_cmd的各种实现方法及优劣（subprocess.Popen, os.system和commands.getstatusoutput）](https://blog.csdn.net/yygydjkthh/article/details/37566155)

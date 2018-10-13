## 建立环境

* [指导书](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Manual+Page+of+Localization+Refactor+May+31th+2018&spaceKey=RRT)

* [How to download dependency repository artifacts?](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=51676609)

* [Jfrog CMD Installation & Usage](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=42537772)

* [安装opencl](https://confluence.ygomi.com:8443/display/RRT/How+to+Set+Up+OpenCL+Compilation+Environment+for+FindOpenCL.cmake+in+CMake3.5)

* [Introduce sysStar tool](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Introduce+sysStar+tool&spaceKey=RRT)

* [Install Docker in Ubuntu](https://confluence.ygomi.com:8443/display/RDC/Install+Docker+in+Ubuntu)
## 虚拟机环境（最终环境没有建好，algorithm_common编译不过，可以通过jfog拉编好的库来规避）
* 安装库
  >```
  >sudo apt-get install libusb-1.0-0-dev
  >sudo apt-get install libudev-dev
  >sudo apt-get install libpcap-dev
  >```
* 编译core/common出错
  >```
  >#解决办法：
  >cp rdb-tools/core/common/thirdParty/eigen/cmake/FindEigen3.cmake  /usr/local/share/cmake-3.5/Modules/
  >```
* 解决db版本问题
  >```
  >#拷贝这两个文件到指定目录下（标哥提供，适配old db版本）
  >SectionMapDef.h
  >SnippetDef.h
  >core/algorithm_common/dist/x64/include
  >#然后重新编译（要用到dist下的include文件）
  >core/algorithm_vehicle_localization

## docker环境
* 命令
  >```
  >docker run -it --name master-build -v "${PWD}":/data -w /data dockerhub.ygomi.com/rdb:latest bash
  >```
* 解决依赖问题
  >```
  ># 需要重新编译data-receiver
  >git clone ssh://git@stash.ygomi.com:7999/as/data-receiver.git
  ># 编译data-receiver需要rdb-device-base-rules（由标哥提供）
  >framework/device/rdb-device-base-rules
  >```
* 解决db版本问题
  >```
  >#拷贝这两个文件到指定目录下（标哥提供，适配old db版本）
  >SectionMapDef.h
  >SnippetDef.h
  >core/algorithm_common/dist/x64/include
  >#然后重新编译（要用到dist下的include文件）
  >core/algorithm_vehicle_localization

## linux
* [linux中的ldd命令简介](https://blog.csdn.net/stpeace/article/details/47069215)

## C++
* [析构函数是否必须为虚函数？什么情况下才应该定义析构函数为虚函数？](https://blog.csdn.net/zhangqk2016/article/details/51849535)
* [C/C++中#pragma once的使用](https://blog.csdn.net/fengbingchun/article/details/78696814)
* [C++ 中using 的使用](https://blog.csdn.net/shift_wwx/article/details/78742459)
* [cpp——类——声明 定义 实现](https://blog.csdn.net/mardax/article/details/54948173)
  >类申明只能使用指针引用类型
  >类定义才能使用成员函数（只定义类，不定义成员函数）
* [声明并定义相同类](https://blog.csdn.net/eclipser1987/article/details/7516968)
  >不会报错，会替代，造成问题
* [为什么类的定义应当写在头文件中,从而被多个源文件包含](https://blog.csdn.net/baoxiaofeicsdn/article/details/48338515)
  >如果对同一个类的两个定义完全相同且出现在不同编译单位，会被当作同一个定义
  >定义了类，但是类的实现在其他位置，编译时，编译器不会去找类的实现，链接时编译器才会去寻找这个类的实现
* [c++编译过程简述](https://blog.csdn.net/fl2_pigy/article/details/80640352)
  >内部链接的符号不能在别的编译单元中使用。但不同的编译单元可以拥有同样的名称的符号
* [头文件中写类的实现出现函数重复定义的问题](https://blog.csdn.net/dengm155/article/details/51692285)
  >inline函数,class和模板类函数被多次包含的情况下，编译器会自动把他们认为是同一个函数，不会发生二次定义的问题。前提是他们一模一样
* [C/C++: 强符号、弱符号与链接](http://blog.sina.com.cn/s/blog_6e32babb0102v0p9.html)
  >成员函数定义在头文件中的时候,不会导致链接问题(头文件被多个.cpp include, 每个cpp都调用到了这个成员函数,那么相应的每个.o 里都有这个成员函数的二进制代码, link完成后,肯定只能剩下一份, 那么这有好几份,岂不冲突! 正是由于这个强弱性, 所以才没事.)
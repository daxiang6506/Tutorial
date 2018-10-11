## 建立环境
* [How to download dependency repository artifacts?](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=51676609)
* [Jfrog CMD Installation & Usage](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=42537772)
* [代码build](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Manual+Page+of+Localization+Refactor+May+31th+2018&spaceKey=RRT)
* 安装库
  ```
  sudo apt-get install libusb-1.0-0-dev
  sudo apt-get install libudev-dev
  sudo apt-get install libpcap-dev
  ```
* 编译core/common出错
  >解决办法：
  >cp rdb-tools/core/common/thirdParty/eigen/cmake/FindEigen3.cmake  /usr/local/share/cmake-3.5/Modules/
* [安装opencl](https://confluence.ygomi.com:8443/display/RRT/How+to+Set+Up+OpenCL+Compilation+Environment+for+FindOpenCL.cmake+in+CMake3.5)

## C++
* [析构函数是否必须为虚函数？什么情况下才应该定义析构函数为虚函数？](https://blog.csdn.net/zhangqk2016/article/details/51849535)
* [C/C++中#pragma once的使用](https://blog.csdn.net/fengbingchun/article/details/78696814)
* [C++ 中using 的使用](https://blog.csdn.net/shift_wwx/article/details/78742459)
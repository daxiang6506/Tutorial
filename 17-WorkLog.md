## 环境

* run simulator

  ```bash
  sudo home/roaddb/code/framework/device/rdb-tools-debug-tools/dist/x64/bin/rosplay-simulator
  -g 3
  -u 5
  -f /home/roaddb/shiyu/696_data/696rosbag/2018-05-13_T_13-57-25.182_GMT_L2R_C_L4_R.bag
  -d p20p1
  -t 10.69.140.181
  -m d0:4c:c1:02:4e:2a
  -k
  ```

  ```bash
  ifconfig
  p20p1     Link encap:Ethernet  HWaddr d0:4c:c1:02:4e:2a
  ```

## 资源

* ABOX
  > 10.69.140.181   一般标哥和xiangqi会用  
  > 10.69.140.220 一般强哥会用  
  > 10.69.140.197  做demo 不能动  
  > 10.69.143.161 三个组的测试在用

## 工具使用

* [Klocwork Test Manual](https://confluence.ygomi.com:8443/display/RRT/Klocwork+Test++Manual)
  >Klockwork:
  >kw_user6   sys2017!  10.69.130.170  
  >[Klocwork Filters](https://confluence.ygomi.com:8443/display/RQA/Klocwork+Filters)

* [How to use Qt5.9 to build TimeStampMonitor](https://confluence.ygomi.com:8443/pages/viewpage.action?title=How+to+use+Qt5.9+to+build+TimeStampMonitor&spaceKey=RRT)

## 信息

* [System High-level Design for EKF Based RT Localisation](https://confluence.ygomi.com:8443/pages/viewpage.action?title=System+High-level+Design+for+EKF+Based+RT+Localisation&spaceKey=RRT)

* [Manual Page for Localization develop branches](https://confluence.ygomi.com:8443/display/RRT/Manual+Page+for+Localization+develop+branches)

* [How to download dependency repository artifacts?](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=51676609)

## 杂项

* [Localization Software Version Test and Acceptance Standard](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Localization+Software+Version+Test+and+Acceptance+Standard&spaceKey=RRT)

* Next Generation Data Collection Solution， 对输入数据的质量检查可以采用工具Multi-SensorFusionPre 来做。会检查RTV帧数，IMU GPS 时偏，IMU GPS 相关性，帧率，最小帧间间隔，最大帧间间隔，RTV IMU 频偏，RTV IMU 时偏，RTV IMU 相关性，IMU RTV 比率。

* pybind11封装C++数据库解析接口，调试编译成Python可调用的动态库，目前动态库已生成，可导入python

* [Sensor Data File Specification](https://confluence.ygomi.com:8443/display/RRT/Sensor+Data+File+Specification)

* [BA Based Localization 模块介绍](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=57476512)

## 任务

* Klockwork:
  >`kw_user6   sys2017!  10.69.130.170`  
  >[Klocwork Test Manual](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Klocwork+Test++Manual&spaceKey=RRT)

* DB选点问题
  >提取关键帧方位角信息，与当前帧比较，选择方向一致（100度以内）  
  >>数据库内关键帧包含的R为世界坐标系（W）  
  >>关键函数`transferCoordinateG2B()`世界坐标系（W）转IMU坐标系（B）  
  >>关键函数`Rbn2angC(B系下R，输出（方向角,...)` R转方向角  
  >
  >得到的位姿与DB中的高度与航向角差异大，则reset

* NaN问题

  ```c++
  ImuGpsFusion.cpp

  LOG_TRACE << "[INS] Update, P_bG:"<<insState_.P_bG_<<"  V_bG:"<<insState_.V_bG_;  
  ```

## 任务（suspend）

* bin file分析工具
  >feature/RDB-35131-pmba-multi-thread-loc-performance-analysis-tools  
  >localization/core/tools/others/ThreadLocPA
  >已经合并入master  
  >已经有更新  
  >>统计了线程中mod先后的模式，默认选择出现次数最多的模式画stack图，修改了一个统计项的bug  
  >>尝试将所有线程起始到结束画在一个图中，还是由于end点可能有多个的问题难以表达清楚，还是得切分为frame再处理  
  >>尝试用`bokeh`画交互图  
  >>>[bokeh](https://bokeh.pydata.org/en/latest/docs/user_guide/quickstart.html)  
  >>>[github](https://github.com/bokeh/bokeh-notebooks)

## 线索

* roadDBCore::ThreadSafeQueue
* roadDBCore::LockFreeLoopQueue
* roadDBCore::pushSyncEvent(RawDataAlignEvent_t(spPackedObject->frameIdx));
* LocDbAlgorithm::filterKeyframeByBatchID


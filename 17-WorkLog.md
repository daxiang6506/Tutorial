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

## 工具

* [How to use Qt5.9 to build TimeStampMonitor](https://confluence.ygomi.com:8443/pages/viewpage.action?title=How+to+use+Qt5.9+to+build+TimeStampMonitor&spaceKey=RRT)
## 信息

* [Localization Software Version Test and Acceptance Standard](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Localization+Software+Version+Test+and+Acceptance+Standard&spaceKey=RRT)

* [Paper Reading - Weekly Reading - 2018 November Week1~2](https://confluence.ygomi.com:8443/display/RRT/Paper+Reading+-+Weekly+Reading+-+2018+November+Week1~2)

* [Manual Page for Localization develop branches](https://confluence.ygomi.com:8443/display/RRT/Manual+Page+for+Localization+develop+branches)

* 目前我们正在考虑如何测试 Next Generation Data Collection Solution， 对输入数据的质量检查可以采用工具Multi-SensorFusionPre 来做。会检查RTV帧数，IMU GPS 时偏，IMU GPS 相关性，帧率，最小帧间间隔，最大帧间间隔，RTV IMU 频偏，RTV IMU 时偏，RTV IMU 相关性，IMU RTV 比率。

* pybind11封装C++数据库解析接口，调试编译成Python可调用的动态库，目前动态库已生成，可导入python

* [Sensor Data File Specification](https://confluence.ygomi.com:8443/display/RRT/Sensor+Data+File+Specification)

* [BA Based Localization 模块介绍](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=57476512)

## 任务

* DB选点问题

* NaN问题

  ```c++
  ImuGpsFusion.cpp

  LOG_TRACE << "[INS] Update, P_bG:"<<insState_.P_bG_<<"  V_bG:"<<insState_.V_bG_;
  ```

## 线索

* roadDBCore::ThreadSafeQueue
* roadDBCore::LockFreeLoopQueue
* roadDBCore::pushSyncEvent(RawDataAlignEvent_t(spPackedObject->frameIdx));
* LocDbAlgorithm::filterKeyframeByBatchID
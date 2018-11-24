* Abox

  ```bash
  ssh roaddb@10.69.140.220
  Test1234
  test1234
  test123
  Test123

  pull_code_build_new_framework_debug.sh
  ```

* [Linhong's Work](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Linhong%27s+Work&spaceKey=RRT)
  >[Segment Detailed Design](https://confluence.ygomi.com:8443/display/RRT/Segment+Detailed+Design)  
  >
  >[Transform between Absolute Coordinate (Geodetic coordinate) and Relative Coordinate](https://confluence.ygomi.com:8443/display/RDD/Transform+between+Absolute+Coordinate+%28Geodetic+coordinate%29+and+Relative+Coordinate)
  >
  >```
  >readelf -d libdataRecv.so
  >
  >ldd /data/localization/core/algorithm_vehicle_localization/../../framework/device/data-receiver/dist/x64/lib/libdataRecv.so
  >
  >nm libdataRecv.so | grep data_checkPc
  >
  >cp localization/framework/device/roaddb_logger/dist/x64/lib/libroadDB_logger.so framework/device/roaddb_logger/dist/x64/
  >
  >./DBConverter -t product -s /data/localization/gm/London/ -e debug -d .
  >```
* db转换工具编译顺序： 
  >core/common  
  >core/algorithm_common  
  >core/algorithm_sam  
  >core/algorithm_server_3  
  >core/server  
  >core/tools
* 单元测试：（localization切换到feature/RDB-33778-fix-eigen-alignment-issue可以跑单元测试）
  >./build.sh -ar  
  >./unit_test_build.sh  
  >./unit_test.sh  
  >[scp -r test@10.69.140.249:/home/test/master_code/core/algorithm_vehicle_localization/unit_test/res/loc_seg_db_dir_1 .   
  >test1  
  >loc_seg_db_dir_1  debugdb  
  >localization/core/algorithm_vehicle_localization/unit_test/res  
  >unit_test_build.sh -s 可视化  
  >docker 下不能使用-s选项
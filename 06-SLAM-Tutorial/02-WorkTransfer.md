* Abox

* [Linhong's Work](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Linhong%27s+Work&spaceKey=RRT)
  >[Segment Detailed Design](https://confluence.ygomi.com:8443/display/RRT/Segment+Detailed+Design)  
  >
  >[Transform between Absolute Coordinate (Geodetic coordinate) and Relative Coordinate](https://confluence.ygomi.com:8443/display/RDD/Transform+between+Absolute+Coordinate+%28Geodetic+coordinate%29+and+Relative+Coordinate)
  >
  >```
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
  >test1  
  >loc_seg_db_dir_1  debugdb  
  >localization/core/algorithm_vehicle_localization/unit_test/res  
  >unit_test_build.sh -s 可视化  
  >docker 下不能使用-s选项
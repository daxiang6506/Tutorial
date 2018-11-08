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
* 编译顺序： 
  >core/common  
  >core/algorithm_common  
  >core/algorithm_sam  
  >core/algorithm_server_3  
  >core/server  
  >core/tools
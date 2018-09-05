## 常用linux命令
* 定位文件
  ```
  locate
  ```
* 查看CPU使用率
  ```
  sar -u 1 5
  ```
  >间隔1秒采集5次
* 查看网卡流量
  ```
  sar -n DEV 1 1
  ```
  >[Linux查看实时网卡流量的几种方式](https://www.jianshu.com/p/b9e942f3682c)
* 查询进程号
  ```
  pgrep -f "tensorboard"
  ```
  >
* kill进程
  ```
  pkill -f "tensorboard"
  ```
  >
* $
  ```
  # 执行date命令，返回执行结果给变量todaydate
  todaydate=$(date +%Y%m%d)
  ```
  ```
  # 取值并打印
  echo ${PATH}
  ```
  ```
  # 表示所有脚本参数的内容
  $@
  ```
  ```
  # 表示返回所有脚本参数的个数
  $#
  ```
  >
* touch
  ```
  
  ```
  >touch命令有两个功能：一是用于把已经存在文件的时间标签更新为系统当前时间，它们的数据将原封不动的保留下来；二是用来创建新的空文件。
* >
  ```
  echo "Raspberry" > test.txt
  ```
  >覆盖文件原内容并重新输入内容，若文件不存在则创建文件
* source
  >[ref](https://www.cnblogs.com/ThatsMyTiger/p/6865817.html)
  ```
  
  ```
  >
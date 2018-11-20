## ubuntu
* [ubuntu自带截图工具](https://blog.csdn.net/qq_38880380/article/details/78233687)
## 常用linux命令
* [Linux下找不到动态库解决，添加rpath](https://blog.csdn.net/baidu_17611285/article/details/82427359)
* [Linux Shell脚本编程－－xargs命令详解](https://blog.csdn.net/xifeijian/article/details/9286189)
* [最常用的也是最容易忘记的Shell知识](https://blog.csdn.net/jewes/article/details/8247743)
* [getopts用法](http://blog.chinaunix.net/uid-22566367-id-381953.html)

* ps -e | grep ssh

* awk的用法

  ```bash
  lscpu | grep "^CPU(s):" | awk '{print $2}'
  echo "first_second_third " | awk -F'_' '{ print NF }'

  ```

* 取得当前脚本所在的目录  
  f 选项可以递归跟随给出文件名的所有符号链接以标准化，除最后一个外所有组件必须存在。  
  简单地说，就是一直跟随符号链接，直到非符号链接的文件位置，限制是最后必须存在一个非符号链接的文件

  ```bash
  $(dirname $(readlink -f $0))
  $(dirname `readlink -f $0`)
  name=$0
  dir=$(dirname ${name})
  ```

* 取得当前脚本的名字

  ```bash
  declare me=`basename $0` （注意，`是和~同一个键的那个字符）
  ```

* 取得当前用户的用户名

  ```bash
  declare current_user=$(id -un)
  ```

* 去路径

  ```bash
  path="target/word.doc"
  echo ${path#*/}
  ```

* 去掉后缀得到文件名

  ```bash
  file=foo.tar.gz
  echo ${file%.tar.gz}
  ```

* []和里面的条件直接必须有空格.  目录是否存在用-d. 文件不存在，在-f 前面加上!

  ```bash
  if [ -f $script_dir/unit_test_build.sh ]; then
    bash $script_dir/unit_test_build.sh
    error_code =  $?
    if [ $error_code -ne 0 ];then
    echo "compile UT failed!!! not all UTs compile successed!!!"
      exit $error_code
    fi
  fi
  ```

* 判定一个目录是否为空

  ```bash
  if [[ "$(ls -A $WSPACE_ROOT/$wspacename)" ]]; then
    echo "folder not empty"
  fi
  ```  

* 大小写转换

  ```bash
  x="HELLO"
  echo $x  # HELLO

  y=${x,,}
  echo $y  # hello

  y=${x,}
  echo $y  # hELLO

  z=${y^^} 
  echo $z  # HELLO

  z=${y^} 
  echo $z  # Hello 
  ```

* 某个字符串是不是以特定字符串开始

  ```bash
  var="# this is comments"
  [[ $var == "#"* ]] && echo "line starts with # is ignored."
  ```

* scp 源 目的
  >`apt-get install openssh-server`

  ```bash
  scp -r ./roaddb_video roaddb@10.69.141.31:/home/roaddb/wanxianlong/framework/device
  scp -r test@10.69.140.249:/home/test/Documents/sprint-2018-10-19/London .
  scp -r usr@10.69.140.183:/home/usr/repo/sophomore/localization/framework/device/roaddb_logger .
  ```

* 软连接

  ```bash
  # 删除软连接
  rm -rf symbolic_name
  # 建立软连接
  ln -s source dist
  # 建立硬连接
  ln source dist
  ```

* ubuntu查看apt安装文件位置

  ```bash
  dpkg -L liblapack-dev
  dpkg -l | grep ssh
  ```

* 定位文件

  ```bash
  locate
  ```

* 查看CPU使用率

  ```bash
  sar -u 1 5
  ```

  >间隔1秒采集5次
* 查看网卡流量

  ```bash
  sar -n DEV 1 1
  ```

  >[Linux查看实时网卡流量的几种方式](https://www.jianshu.com/p/b9e942f3682c)
* 查询进程号

  ```bash
  pgrep -f "tensorboard"
  ```

* kill进程

  ```bash
  pkill -f "tensorboard"
  ```

* $

  ```bash
  # 执行date命令，返回执行结果给变量todaydate
  todaydate=$(date +%Y%m%d)
  ```

  ```bash
  # 取值并打印
  echo ${PATH}
  ```

  ```bash
  # 表示所有脚本参数的内容
  $@
  ```

  ```bash
  # 表示返回所有脚本参数的个数
  $#
  ```

  ```bash
  # 表示第一个参数
  $0 ${0}
  ```

  ```bash
  # 表示"最后一次执行命令"的退出状态.0为成功,非0为失败
  $?
  ```

* touch
  >touch命令有两个功能：一是用于把已经存在文件的时间标签更新为系统当前时间，它们的数据将原封不动的保留下来；二是用来创建新的空文件。
* echo

  ```bash
  echo "Raspberry" > test.txt
  ```

  >覆盖文件原内容并重新输入内容，若文件不存在则创建文件
* source
  >[ref](https://www.cnblogs.com/ThatsMyTiger/p/6865817.html)
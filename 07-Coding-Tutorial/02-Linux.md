# Linux

## ubuntu

* [Linux系统 apt-get 命令的使用：安装、更新、卸载软件包](https://blog.csdn.net/xietansheng/article/details/80044644)
* [ubuntu下的apt-get内网本地源的搭建](https://www.cnblogs.com/czalinux/p/6188938.html)
* [du-查看文件夹大小-并按大小进行排序](https://blog.csdn.net/jiaobuchong/article/details/50272761cd)
* [ubuntu系统下安装ftp相关客户端工具之Filezilla](https://blog.csdn.net/weixin_42835066/article/details/87628691)
* [How to install massif-visualizer on Ubuntu 16.04](https://www.howtoinstall.co/en/ubuntu/xenial/massif-visualizer)
* [How to install kcachegrind on Ubuntu 16.04](https://www.howtoinstall.co/en/ubuntu/xenial/kcachegrind)
* [ubuntu16.04如何安装搜狗输入法](https://jingyan.baidu.com/article/642c9d341b3ccb644a46f7ac.html)
* [ubuntu自带截图工具](https://blog.csdn.net/qq_38880380/article/details/78233687)
* [Ubuntu安装钉钉](https://blog.csdn.net/gozs_cs_dn/article/details/80230935)

## reference

* [【Linux】lsof 命令，记一次端口占用查询](https://www.cnblogs.com/liuyongcn/p/5433139.html)
* [sed 命令](https://www.ibm.com/support/knowledgecenter/zh/ssw_aix_71/com.ibm.aix.cmds5/sed.htm)
* [Linux sed命令](http://www.runoob.com/linux/linux-comm-sed.html)
* [Linux下找不到动态库解决，添加rpath](https://blog.csdn.net/baidu_17611285/article/details/82427359)
* [Linux Shell脚本编程－－xargs命令详解](https://blog.csdn.net/xifeijian/article/details/9286189)
* [最常用的也是最容易忘记的Shell知识](https://blog.csdn.net/jewes/article/details/8247743)
* [getopts用法](http://blog.chinaunix.net/uid-22566367-id-381953.html)
* [ssh-copy-id三步实现SSH无密码登录和ssh常用命令](https://blog.csdn.net/liu_qingbo/article/details/78383892)
* [2>/dev/null和>/dev/null 2>&1和2>&1>/dev/null](https://blog.csdn.net/zhongqi2513/article/details/78613768)
* [Linux Source命令及脚本的执行方式解析](https://www.cnblogs.com/ThatsMyTiger/p/6865817.html)
* [git try](http://try.github.io/)

## 常用linux软件

* 录屏软件`sudo apt-get install kazam`

## 常用linux命令

* `awk -F',' -v OFS=',' '{print "GPS:"$7,$2,$3,$4,$5,$6,$7}' 2019-02-21_T_08-20-45.759_GMT4.gps > 1.txt`

* `df -h`

* `du -sh *`

* 支持scp，ssh server
  >`sudo apt-get install openssh-server`
  
* `./build.sh -a 1>log.log 2>&1`

* less
   / 字符串	       向下搜索“字符串”的功能
   ? 字符串	       向上搜索“字符串”的功能
   n	            重复前一个搜索（与 / 或 ? 有关）
   N	            反向重复前一个搜索（与 / 或 ? 有关）
   
* kill

  ```cpp
  void loc_panel::stop_loc(const std::string &procName)
  {

    kill_proc(procName, 9, true);
    std::stringstream ss;
    ss.str("");
    ss << "cd /home/roaddb; "
       << "sudo ./stop_loc.sh > /dev/null 2>&1;";

    std::vector<std::string> ret = con->do_cmd(ss.str(), true, true);
    if(ret.size() == 0)
        ui->status->setText("stop localization success.");
    else
        ui->status->setText("stop localization fail.");
  }

  ```cpp

* ssh

  ```bash
  REMOTE_IP=$1
  if [ ! -f ~/.ssh/id_rsa.pub ];then
    ssh-keygen
  fi
  ssh-copy-id -i ~/.ssh/id_rsa.pub  roaddb@${REMOTE_IP}
  scp run_loc.sh roaddb@${REMOTE_IP}:/home/roaddb
  scp stop_loc.sh roaddb@${REMOTE_IP}:/home/roaddb
  sudo echo "roaddb ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
  ```

  ```bash
  #!/bin/sh
  pids=`ps -ef | grep -v grep | grep "MultiThreadsLoc" | sed -E "/[A-Za-z]* *([0-9]*).*/s//\\1/"`
  for pid in $pids
    do
     sudo kill -2 $pid
     sudo kill -3 $pid
    done
  sleep 1
  ret=`ps -ef | grep -v grep | grep "MultiThreadsLoc" | sed -E "/[A-Za-z]* *([0-9]*).*/s//\\1/"`
  echo "$ret"
  ```

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

  >source命令通常用于重新执行刚修改的初始化文件，使之立即生效，而不必注销并重新登录
* source
  >[ref](https://www.cnblogs.com/ThatsMyTiger/p/6865817.html)
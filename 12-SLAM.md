## 参考
* [slum book](https://github.com/gaoxiang12/slambook)
* [virtul box 挂载文件夹](https://blog.csdn.net/a962804835/article/details/72820355)
* [CMake如何查找链接库---find_package的使用方法](https://blog.csdn.net/u011092188/article/details/61425924)
* [CMake实践》笔记二：INSTALL/CMAKE_INSTALL_PREFIX](https://blog.csdn.net/primeprime/article/details/53020147)
* [hpp](https://blog.csdn.net/davidhsing/article/details/4222227)
* [ninja](https://www.jianshu.com/p/d118615c1943)
* [欧拉角](https://blog.csdn.net/csxiaoshui/article/details/65437633)
* [eigen](http://eigen.tuxfamily.org/index.php?title-Main_Page)
  >矩阵库
* [pangolin](https://github.com/stevenlovegrove/Pangolin)
  >OpenGL封装库
* [pangolin安装及其使用](https://blog.csdn.net/c602273091/article/details/65441315)
* [C++里面ostream是干什么的](https://zhidao.baidu.com/question/584182022.html?qbl=relate_question_3&word=ostream%26%20operator)
* [Sophus](https://github.com/strasdat/Sophus)
  >李群库
* [PCL](http://pointclouds.org)
  >Point Cloud Library
* [Ceres](https://github.com/ceres-solver/ceres-solver)
  >通用最小二乘问题求解库

## action
```
#宿主机改变权限
sudo chmod -R 777 /home/usr/repo/
#虚拟机创建目录
sudo mkdir /mnt/xuc
#改变目录权限
sudo chmod -R 777 /mnt/xuc

#在virtual box里创建shared folders，见图

#挂载宿主机目录到虚拟机目录
sudo mount -t vboxsf repo /mnt/xuc

#取消挂载
sudo umount /mnt/xuc
#删除目录
sudo rm -rf /mnt/xuc
```
* ![vbox](_images/vbox.png)
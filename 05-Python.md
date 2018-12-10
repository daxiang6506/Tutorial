# python
## pycharm
* [Docker-Compose: Getting Flask up and running](https://blog.jetbrains.com/pycharm/2017/03/docker-compose-getting-flask-up-and-running/)
* [Using Docker in PyCharm](https://blog.jetbrains.com/pycharm/2015/12/using-docker-in-pycharm)
* 新版本的Pycharm可以使用更好用的Docker Compose方式来运行，要指定两个编排文件，一个用于部署，一个用于debug，debug模式需要指定：
  ```
  if __name__ == '__main__':
    app.debug = True
    app.run(host='0.0.0.0')
  ```
* Pycharm使用docker时，需要配置docker API，windows中配置为主机加端口号，unix配置为 `docker.sock` 文件。
  ![pycharm-docker](_images/pycharm-docker.png)
* 运行flask程序时，要指定host为0.0.0.0主机才能访问到docker中的内容.  
  ![flask](_images/pycharm-flask.png)
* 运行Django程序的时候，host要指定为0.0.0.0才能访问docker中的内容，端口会自动映射，映射规则就是7002:7002，同端口映射.  
  ![Django](_images/pycharm-Django.png)

## matplotlib
* [colormaps_reference](https://matplotlib.org/examples/color/colormaps_reference.html)

## reference

* [Python使用struct处理二进制](https://www.cnblogs.com/gala/archive/2011/09/22/2184801.html)
* [python 按二维数组的某行或列排序 (numpy lexsort)](https://www.cnblogs.com/liyuxia713/p/7082091.html)
* [Python中numpy的where()函数](http://www.cnblogs.com/oxxxo/p/6129294.html)
* [Numpy where function multiple conditions](https://stackoverflow.com/questions/16343752/numpy-where-function-multiple-conditions)
* [Box plot with min, max, average and standard deviation](https://stackoverflow.com/questions/33328774/box-plot-with-min-max-average-and-standard-deviation)
* [Python format 格式化函数](http://www.runoob.com/python/att-string-format.html)
* [Matplotlib legends in subplot](https://stackoverflow.com/questions/27016904/matplotlib-legends-in-subplo)
* [python中matplotlib的颜色及线条控制](https://www.cnblogs.com/darkknightzh/p/6117528.html)
* [Python数据分析之可视化一matplotlib(常用方法)](https://blog.csdn.net/qq_37512382/article/details/79401864)
* [从零开始学Python数据分析【17】-- matplotlib(面积图)](https://www.jianshu.com/p/a1982983e970)
* [Matplotlib(二) — 常见的图表](https://blog.csdn.net/love667767/article/details/79250510)
* [Python中一个for循环循环多个变量](https://blog.csdn.net/theonegis/article/details/49404809)
* [Most efficient way to reverse a numpy array](https://stackoverflow.com/questions/6771428/most-efficient-way-to-reverse-a-numpy-array)

# python

## 资源

* [Python 3 教程](http://www.runoob.com/python3/python3-tutorial.html)

## pycharm

* [Docker-Compose: Getting Flask up and running](https://blog.jetbrains.com/pycharm/2017/03/docker-compose-getting-flask-up-and-running/)
* [Using Docker in PyCharm](https://blog.jetbrains.com/pycharm/2015/12/using-docker-in-pycharm)
* 新版本的Pycharm可以使用更好用的Docker Compose方式来运行，要指定两个编排文件，一个用于部署，一个用于debug，debug模式需要指定：

  ```python
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

* [python 字符串格式化](https://www.cnblogs.com/xxby/p/5571620.html)  
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

## pandas

* [How to Add Incremental Numbers to a New Column Using Pandas](https://stackoverflow.com/questions/38862293/how-to-add-incremental-numbers-to-a-new-column-using-pandas)

* [Pandas通过reset_index()函数可以将groupby()的分组结果转换成DataFrame对象](https://www.cnblogs.com/princessd8251/articles/7658577.html)

* [pandas contact 之后，一定要记得用reset_index去处理index,不然容易出现莫名的逻辑错误](https://blog.csdn.net/lujiandong1/article/details/52929090)

* [pandas通过loc生成新的列](https://blog.csdn.net/qq_36523839/article/details/80502574)

* [Pandas 操作多个列进行运算，并生成新列的方法](https://blog.csdn.net/weixin_42493346/article/details/80744159)

* [pandas 的 行、列重排序 reindex()](https://www.jianshu.com/p/07e7d9710773)

## ROC

* [ROC和AUC介绍以及如何计算AUC](http://www.360doc.com/content/16/0508/21/32866621_557382331.shtml)

* [分类性能度量指标 : ROC曲线、AUC值、正确率、召回率、敏感度、特异度](https://blog.csdn.net/tanzuozhev/article/details/79109311)
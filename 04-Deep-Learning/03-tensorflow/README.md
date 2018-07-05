# tensorflow
## tensorflow语法
### 张量/变量
* 张量的第一个属性名字不仅是一个张量的唯一标识符，它同样也给出了张量是如何计算出来的。
* 张量和计算图上所代表的计算结果是对应的
张量的命名“node: src_output”
* 在TensorFlow中，变量的声明函数tf.Variable是一个运算，这个运算的结果就是一个张量，这个张量就是变量，所以变量只是一种特殊的张量

### operation
* [初步理解 TensorFlow 的 operation](https://zhuanlan.zhihu.com/p/3239903)
   1. 所有的常量、变量和计算的操作都是 OP  
   2. 变量包含的 OP 更加复杂
   3. 可以通过 graph.get_operation_by_name，或者 x.op 的方式获得该 OP 的详细信息
   4. OP 可以简单理解为一个个小份的特定任务，通过并发地执行Kernel实现

## 模型
* [TensorFlow 版本 inception v3 网络代码解读](https://zhuanlan.zhihu.com/p/34055904)
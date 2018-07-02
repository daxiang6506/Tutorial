## Tensorflow Mnist手写数字识别Go实战
* [链接](http://sineyuan.github.io/2017/03/02/tensorflow-mnist-pratice/)
* [github](https://github.com/SineYuan/tensorflow-demo)
### 注意事项
* 需要注意的是训练并导出模型需要使用1.0.0版本，不然有兼容性问题

### debug
* 修改输入tensor签名名称
  ```
  rpc error: code = InvalidArgument desc = input tensor alias not found in signature: x1
  ```
* 修改输出tensor签名名称
  ```
  can not find output data with label y
  ```
* 修改输入tensor签名数据长度
  ```
  rpc error: code = Internal desc = Invalid header field value "input to reshape is a tensor with 1260 values, but the requested shape requires a multiple of 588\n\t [[Node: Reshape=Reshape[T=DT_FLOAT,Tshape=DT_INT32,_device=\"/job:localhost/replica:0/task:0/cpu:0\"](Relu_2, Reshape/shape)]]
  ```
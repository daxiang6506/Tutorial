## 构建并用 TensorFlow Serving 部署 Wide & Deep 模型
* [链接](https://www.jianshu.com/p/2fffd0e332bc)
* [github](https://github.com/edvardHua/Articles)

### 注意事项
* [sineyuan/tensorflow_model_server](https://hub.docker.com/r/sineyuan/tensorflow_model_server/)
  >tensorflow model server built from [https://github.com/tensorflow/serving](https://github.com/tensorflow/serving)
* [bitnami/tensorflow-serving](https://hub.docker.com/r/bitnami/tensorflow-serving/)
  >Bitnami Docker Image for TensorFlow Serving
  [https://github.com/bitnami/bitnami-docker-tensorflow-serving](https://github.com/bitnami/bitnami-docker-tensorflow-serving)

### debug
* 向签名完全不对的server发起请求
  ```
  rpc error: code = NotFound desc = Servable not found for request:Latest(default)
  ```
* 关闭server，发起请求，过大约30秒，返回错误码
  ```
  rpc error: code = Unavailable desc = all SubConns are in TransientFailure
  ```
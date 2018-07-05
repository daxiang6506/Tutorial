# Tensorflow models
## 参考
* [A quick complete tutorial to save and restore Tensorflow models](http://cv-tricks.com/tensorflow-tutorial/save-restore-tensorflow-models-quick-complete-tutorial/)
* The [freeze_graph.py](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/python/tools/freeze_graph.py) script, which is part of the TensorFlow repository, now serves as a tool that generates a protocol buffer representing a "frozen" trained model, from an existing TensorFlow GraphDef and a saved checkpoint
  >有时候，我们需要将TensorFlow的模型导出为单个文件（同时包含模型架构定义与权重），方便在其他地方使用（如在C++中部署网络）。`tf.train.write_graph()`默认情况下只导出了网络的定义（没有权重），而`tf.train.Saver().save()`导出的文件`graph def`与权重是分离的。`graph def`文件中没有包含网络中的`Variable`值，如果我们能把`Variable`转换为`Constant`，即可达到使用一个文件同时存储网络架构与权重的目标。
* [将TensorFlow的网络导出为单个文件](https://tang.su/2017/01/export-TensorFlow-network/)
* [TensorFlow 保存模型为 PB 文件](https://zhuanlan.zhihu.com/p/32887066)
* [Use serving without any checkpoint](https://github.com/tensorflow/serving/issues/317)
* [网络模型的保存和读取](https://blog.csdn.net/lwplwf/article/details/62419087)
## 关键代码
* ***tf.train.Saver()***
  ```
  saver.save(sess, 'my_test_model')
  ```
  ```
  saver.save(sess, 'my-model', global_step=step,write_meta_graph=False)
  ```
  ```
  saver = tf.train.Saver(max_to_keep=4, keep_checkpoint_every_n_hours=2)
  ```
* ***tf.train.write_graph()***
  ```
  graph = convert_variables_to_constants(sess, sess.graph_def, ["out"])
  tf.train.write_graph(graph, '.', 'graph.pb', as_text=False)
  ```
  ```
  tf.train.write_graph(sess.graph_def, "/tmp/load", "test.pb", False)
  ```
* ***tf.gfile.FastGFile()***
  ```
  constant_graph = graph_util.convert_variables_to_constants(sess, sess.graph_def, ['op_to_store'])
  with tf.gfile.FastGFile(pb_file_path+'model.pb', mode='wb') as f:
    f.write(constant_graph.SerializeToString())
  ```
* ***tf.saved_model.builder.SavedModelBuilder()***
  ```
  builder = tf.saved_model.builder.SavedModelBuilder(pb_file_path+'savemodel')
  builder.add_meta_graph_and_variables(sess, ['cpu_server_1'])
  builder.save()  
  ```
  ```
  with sess.graph.as_default():
      x_op = sess.graph.get_operation_by_name("Placeholder")
      x = x_op.outputs[0]
      pred_op = sess.graph.get_operation_by_name("pred")
      pred = pred_op.outputs[0]

  with sess.graph.as_default():
      prediction_signature = signature_def_utils.build_signature_def(
          inputs={
              "inputs": utils.build_tensor_info(x)
          },
          outputs={
              "pred": utils.build_tensor_info(pred)
          },
          method_name=signature_constants.PREDICT_METHOD_NAME
      )
      builder = saved_model_builder.SavedModelBuilder(export_path)
      builder.add_meta_graph_and_variables(
          sess, [tag_constants.SERVING],
          signature_def_map={
              "predict": prediction_signature,
          })
      builder.save()
  ```
* ***tf.train.import_meta_graph()***
* ***tf.train.latest_checkpoint()***
  ```
  saver = tf.train.import_meta_graph('my_test_model-1000.meta')
  ```
  ```
  saver.restore(sess, tf.train.latest_checkpoint('./'))
  ```
* ***graph.get_tensor_by_name()***
  ```
  w1 = graph.get_tensor_by_name("w1:0")
  ```
* ***tf.import_graph_def()***
  ```
  with gfile.FastGFile("/tmp/load/test.pb",'rb') as f:
    graph_def = tf.GraphDef()
    graph_def.ParseFromString(f.read())
    tf.import_graph_def(graph_def, name='')
  ```
  ```
  with tf.Session() as sess:
    with open('./graph.pb', 'rb') as f:
        graph_def = tf.GraphDef()
        graph_def.ParseFromString(f.read()) 
        output = tf.import_graph_def(graph_def, return_elements=['out:0']) 
        print(sess.run(output))
  ```
  ```
  with tf.Session() as sess:
    with open('./graph.pb', 'rb') as f: 
        graph_def = tf.GraphDef()
        graph_def.ParseFromString(f.read()) 
        output = tf.import_graph_def(graph_def, input_map={'input:0':4.}, return_elements=['out:0'], name='a') 
        print(sess.run(output))
  ```
  ```
  new_input = tf.placeholder(tf.float32, shape=())
  
  with tf.Session() as sess:
      with open('./graph.pb', 'rb') as f: 
          graph_def = tf.GraphDef()
          graph_def.ParseFromString(f.read()) 
          output = tf.import_graph_def(graph_def, input_map={'input:0':new_input}, return_elements=['out:0'], name='a') 
          print(sess.run(output, feed_dict={new_input:4}))
  ```
* ***tf.saved_model.loader.load()***
  ```
  with tf.Session(graph=tf.Graph()) as sess:
    tf.saved_model.loader.load(sess, ['cpu_1'], pb_file_path+'savemodel')
    sess.run(tf.global_variables_initializer())

    input_x = sess.graph.get_tensor_by_name('x:0')
    input_y = sess.graph.get_tensor_by_name('y:0')

    op = sess.graph.get_tensor_by_name('op_to_store:0')

    ret = sess.run(op,  feed_dict={input_x: 5, input_y: 5})
    print(ret)
  ```
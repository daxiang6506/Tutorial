# Tensorflow models
## 参考
* [A quick complete tutorial to save and restore Tensorflow models](http://cv-tricks.com/tensorflow-tutorial/save-restore-tensorflow-models-quick-complete-tutorial/)
* The [freeze_graph.py](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/python/tools/freeze_graph.py) script, which is part of the TensorFlow repository, now serves as a tool that generates a protocol buffer representing a "frozen" trained model, from an existing TensorFlow GraphDef and a saved checkpoint
  >有时候，我们需要将TensorFlow的模型导出为单个文件（同时包含模型架构定义与权重），方便在其他地方使用（如在C++中部署网络）。`tf.train.write_graph()`默认情况下只导出了网络的定义（没有权重），而`tf.train.Saver().save()`导出的文件`graph def`与权重是分离的。`graph def`文件中没有包含网络中的`Variable`值，如果我们能把`Variable`转换为`Constant`，即可达到使用一个文件同时存储网络架构与权重的目标。
* [将TensorFlow的网络导出为单个文件](https://tang.su/2017/01/export-TensorFlow-network/)
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
* ***convert_variables_to_constants()***
* ***tf.train.write_graph()***
  ```
  graph = convert_variables_to_constants(sess, sess.graph_def, ["out"])
  tf.train.write_graph(graph, '.', 'graph.pb', as_text=False)
  ```
* ***tf.train.write_graph()***
  ```
  tf.train.write_graph(sess.graph_def, "/tmp/load", "test.pb", False)
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
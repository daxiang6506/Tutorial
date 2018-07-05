# Tensorflow models
## 参考
* [A quick complete tutorial to save and restore Tensorflow models](http://cv-tricks.com/tensorflow-tutorial/save-restore-tensorflow-models-quick-complete-tutorial/)
* The [freeze_graph.py](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/python/tools/freeze_graph.py) script, which is part of the TensorFlow repository, now serves as a tool that generates a protocol buffer representing a "frozen" trained model, from an existing TensorFlow GraphDef and a saved checkpoint
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
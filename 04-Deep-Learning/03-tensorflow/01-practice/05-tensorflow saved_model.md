# Tensorflow saved_model
* saved_model模块主要用于TensorFlow Serving。TF Serving是一个将训练好的模型部署至生产环境的系统，主要的优点在于可以保持Server端与API不变的情况下，部署新的算法或进行试验，同时还有很高的性能。

## 参考
* [TensorFlow saved_model 模块](https://blog.csdn.net/thriving_fcl/article/details/75213361)
* [Saving and serving your model](https://medium.com/epigramai/tensorflow-serving-101-pt-1-a79726f7c103)
* [Sending requests to your model](https://medium.com/epigramai/tensorflow-serving-101-pt-2-682eaf7469e7)

## 关键代码
* ***get_tensor_by_name()***
* ***build_tensor_info()***
* ***build_signature_def()***
  ```
  # Pick out the model input and output
  a_tensor = sess.graph.get_tensor_by_name(placeholder_name + ':0')
  sum_tensor = sess.graph.get_tensor_by_name(operation_name + ':0')
  
  model_input = build_tensor_info(a_tensor)
  model_output = build_tensor_info(sum_tensor)
  
  # Create a signature definition for tfserving
  signature_definition = signature_def_utils.build_signature_def(
      inputs={placeholder_name: model_input},
      outputs={operation_name: model_output},
      method_name=signature_constants.PREDICT_METHOD_NAME)
  ```
* ***add_meta_graph_and_Variables()***
  ```
  builder = saved_model_builder.SavedModelBuilder('./models/simple_model/1')
  
  builder.add_meta_graph_and_variables(
      sess, [tag_constants.SERVING],
      signature_def_map={
          signature_constants.DEFAULT_SERVING_SIGNATURE_DEF_KEY:
              signature_definition
      })
  
  # Save the model so we can serve it with a model server :)
  builder.save()
  ```
* ***build_tensor_info()***
   ```
   x_wide = tf.placeholder(tf.float32, [None, 10])
   tf.saved_model.utils.build_tensor_info(x_wide)
  
   serialized_tf_example = tf.placeholder(tf.string, name='tf_example')
   tf.saved_model.utils.build_tensor_info(serialized_tf_example)
   ```
* ***FixedLenFeature()***
* ***parse_example()***
   ```
   serialized_tf_example = tf.placeholder(tf.string, name='tf_example')

   feature_configs = {'image/encoded': tf.FixedLenFeature(shape=[], dtype=tf.string),}

   tf_example = tf.parse_example(serialized_tf_example, feature_configs)

   jpegs = tf_example['image/encoded']

   tf.saved_model.utils.build_tensor_info(jpegs)
   ```
* ***make_tensor_proto()***
  ```
  client = ProdClient(host, model_name, model_version)
  
  req_data = [{'in_tensor_name': 'a', 'in_tensor_dtype': 'DT_INT32', 'data': 2}]
  
  prediction = client.predict(req_data, request_timeout=10)
  ```
  ```
  for d in request_data:
    tensor_proto = make_tensor_proto(d['data'], d['in_tensor_dtype'])
    request.inputs[d['in_tensor_name']].CopyFrom(tensor_proto)
  ```
## 读取模型
* 读取已经训练好的Inception-v3模型
  ```
  with gfile.FastGFile(os.path.join(MODEL_DIR, MODEL_FILE), 'rb') as f:
       graph_def = tf.GraphDef()
       graph_def.ParseFromString(f.read())
  bottleneck_tensor, jpeg_data_tensor = tf.import_graph_deg(graph_def, return_elements=[BOTTLENECK_TENSOR_NAME, JPEG_DATA_TENSOR_NAME])
  ```
## 参考
* [TensorFlow直接读取图片和读写TFRecords速度对比](https://zhuanlan.zhihu.com/p/27481108)
* [TensorFlow高效读取数据的方法](https://blog.csdn.net/u012759136/article/details/52232266)
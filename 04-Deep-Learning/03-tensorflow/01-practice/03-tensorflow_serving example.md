## tensorflow_serving example
* [github](https://github.com/tensorflow/serving/tree/master/tensorflow_serving/example)

### 关键代码
* inception_saved_model.py
  ```
  builder.add_meta_graph_and_variables(
      sess, [tf.saved_model.tag_constants.SERVING],
      signature_def_map={
          'predict_images':
              prediction_signature,
          tf.saved_model.signature_constants.
          DEFAULT_SERVING_SIGNATURE_DEF_KEY:
              classification_signature,
      },
      legacy_init_op=legacy_init_op)  
  ```
  >多个签名

* inception_client.py
  ```
  def main(_):
    host, port = FLAGS.server.split(':')
    channel = implementations.insecure_channel(host, int(port))
    stub = prediction_service_pb2.beta_create_PredictionService_stub(channel)
    # Send request
    with open(FLAGS.image, 'rb') as f:
      # See prediction_service.proto for gRPC request/response details.
      data = f.read()
      request = predict_pb2.PredictRequest()
      request.model_spec.name = 'inception'
      request.model_spec.signature_name = 'predict_images'
      request.inputs['images'].CopyFrom(
          tf.contrib.util.make_tensor_proto(data, shape=[1]))
      result = stub.Predict(request, 10.0)  # 10 secs timeout
      print(result)  
  ```
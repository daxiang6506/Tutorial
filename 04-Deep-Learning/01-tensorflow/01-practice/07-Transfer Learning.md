# Transfer Learning
## 案例
* [Inception V3 迁移学习 训练 Fate stay night 人物识别](https://github.com/joliph/InceptionV3_for_Fate)

## 关键代码
* retrain.py
  >`'DecodeJpeg/contents:0'`
   ```
   with gfile.FastGFile(model_filename, 'rb') as f:
     graph_def = tf.GraphDef()
     graph_def.ParseFromString(f.read())
     bottleneck_tensor, jpeg_data_tensor, resized_input_tensor = (
       tf.import_graph_def(graph_def, name='', return_elements=[
           'pool_3/_reshape:0', 'DecodeJpeg/contents:0','ResizeBilinear:0']))
   ```
  >`final_result`
   ```
   final_tensor = tf.nn.softmax(logits, name=final_tensor_name)
   ```
   ```
   output_graph_def = graph_util.convert_variables_to_constants(sess, graph.as_graph_def(), [FLAGS.final_tensor_name])
   with gfile.FastGFile(FLAGS.output_graph, 'wb') as f:
     f.write(output_graph_def.SerializeToString())
   ```
   ```
   parser.add_argument(
    '--final_tensor_name',
    type=str,
    default='final_result',
    help="""\
    The name of the output classification layer in the retrained graph.\
    """
  )
  ```
* label.py
  >`tf.import_graph_def()`
   ```
   with tf.gfile.FastGFile("retrained_graph.pb", 'rb') as f:
    graph_def = tf.GraphDef()
    graph_def.ParseFromString(f.read())
    _ = tf.import_graph_def(graph_def, name='')
   ```
  >`final_result`
   ```
   softmax_tensor = sess.graph.get_tensor_by_name('final_result:0')
   ```
  >`prediction`
   ```
   predictions = sess.run(softmax_tensor, {'DecodeJpeg/contents:0': image_data})
   ```
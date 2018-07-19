# Tensorflow for poets 2
* [链接](https://codelabs.developers.google.com/codelabs/tensorflow-for-poets/#0)

* [github](https://github.com/googlecodelabs/tensorflow-for-poets-2)

* [tensorflow tutorial image retrain](https://www.tensorflow.org/tutorials/image_retraining)

* [Tensorflow MobileNet移动端迁移学习指南](https://yq.aliyun.com/articles/566213)

## 代码
```
python3 -m retrain \
  --bottleneck_dir=tf_files/bottlenecks \
  --how_many_training_steps=500 \
  --model_dir=tf_files/models/ \
  --output_graph=tf_files/retrained_graph.pb \
  --output_labels=tf_files/retrained_labels.txt \
  --image_dir=tf_files/flower_photos
  
python3 -m label_image \
    --graph=tf_files/retrained_graph.pb  \
    --image=tf_files/flower_photos/daisy/3475870145_685a19116d.jpg 
```
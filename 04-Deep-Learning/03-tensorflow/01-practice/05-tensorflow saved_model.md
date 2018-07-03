# Tensorflow saved_model
* [saved_model模块主要用于TensorFlow Serving。TF Serving是一个将训练好的模型部署至生产环境的系统，主要的优点在于可以保持Server端与API不变的情况下，部署新的算法或进行试验，同时还有很高的性能。
](https://blog.csdn.net/thriving_fcl/article/details/75213361)
* 
1. 仅用Saver来保存/载入变量。这个方法显然不行，仅保存变量就必须在inference的时候重新定义Graph(定义模型)，这样不同的模型代码肯定要修改。即使同一种模型，参数变化了，也需要在代码中有所体现，至少需要一个配置文件来同步，这样就很繁琐了。
2. 使用tf.train.import_meta_graph导入graph信息并创建Saver， 再使用Saver restore变量。相比第一种，不需要重新定义模型，但是为了从graph中找到输入输出的tensor，还是得用graph.get_tensor_by_name()来获取，也就是还需要知道在定义模型阶段所赋予这些tensor的名字。如果创建各模型的代码都是同一个人完成的，还相对好控制，强制这些输入输出的命名都一致即可。如果是不同的开发者，要在创建模型阶段就强制tensor的命名一致就比较困难了。这样就不得不再维护一个配置文件，将需要获取的tensor名称写入，然后从配置文件中读取该参数。
经过上面的分析发现，要实现inference的代码统一，使用原来的方法也是可以的，只不过TensorFlow官方提供了更好的方法，并且这个方法不仅仅是解决这个问题，所以还是得学习使用saved_model这个模块。
* 输入输出定义好，signature_name也要定义好,signature_name可能有多个
   #tf.saved_model.utils.build_tensor_info()
  1. 第一种通过placeholder来占位，给出type和shape信息
     ```
     x_wide = tf.placeholder(tf.float32, [None, 10])
     tf.saved_model.utils.build_tensor_info(x_wide)
  
     serialized_tf_example = tf.placeholder(tf.string, name='tf_example')
     tf.saved_model.utils.build_tensor_info(serialized_tf_example)
     ```
  2. 第二种通过tf.parse_example()来生成
     ```
     serialized_tf_example = tf.placeholder(tf.string, name='tf_example'
     feature_configs = {'image/encoded': tf.FixedLenFeature(shape=[], dtype=tf.string),}tf_example = tf.parse_example(serialized_tf_example, feature_configs)
     jpegs = tf_example['image/encoded']
     tf.saved_model.utils.build_tensor_info(jpegs)
     ```
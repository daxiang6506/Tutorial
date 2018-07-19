## docker命令
* 
```
#
docker run -it -p 8888:8888 -p 6006:6006 -v /home/tf:/notebooks/Deep_Learning_with_TensorFlow daxiang6506/tensorflow-tutorial
#
tensorboard --logdir=/modified_mnist_train.log
```
* 
```
#
docker run -p 8888:8888 -p 6006:6006 b.gcr.io/tensorflow/tensorflow ./run_jupyter.sh
#
docker run -p 8881:8888 -p 6001:6006 -it --name="1.0.0" -v /home/tf/1.0.0:/notebooks tensorflow/tensorflow:1.0.0
#
docker run -p 8882:8888 -p 6002:6006 -it --name="1.6.0-devel-py2"  -v /home/tf/1.6.0-devel:/root/notebooks daxiang6506/tensorflow:1.6.0-devel ../run_jupyter.sh --allow-root
#
docker run -p 8883:8888 -p 6003:6006 -it --name="1.6.0-devel-py3"  -v /home/tf/1.6.0-devel-py3:/root/notebooks daxiang6506/tensorflow:1.6.0-devel-py3 ../run_jupyter.sh --allow-root
#
```
* 
```
jupyter notebook --ip=* --allow-root --port=8888
#
locale
locale -a
export LANG="C.UTF-8"
#
docker run -p 8881:8888 -p 6001:6006 -it --name="1.0.0" -v /home/tf/1.0.0:/notebooks daxiang6506/tensorflow:1.0.0
#
docker run -p 8883:8888 -p 6003:6006 --name="1.6.0-devel-py3"  -v C:/Users/Administrator/tensorflow/1.6.0-devel-py3:/root/notebooks daxiang6506/tensorflow:1.6.0-devel-py3 ../run_jupyter.sh --allow-root
```
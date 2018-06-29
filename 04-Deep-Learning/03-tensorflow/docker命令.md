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
* Anaconda
```
#
docker run -p 8888:8888 -p 6006:6006 -it --name="Anaconda" -v C:/Users/Administrator/tensorflow/Anaconda3-5.1.0/TensorFlow-Tutorials:/root/notebook daxiang6506/tensorflow:Anaconda3-5.1.0
#
conda create --name tf python=3
conda activate tf
source activate tf
pip install -r requirements.txt
cd /root/notebook
jupyter notebook --ip=* --allow-root --port=8888
tensorboard --logdir=/root/log
#
export PATH="/root/Anaconda3-5.1.0/bin:$PATH"
conda info --env
source activate tf
tensorboard --logdir=log

#
 ~/Anaconda3-5.1.0/bin/conda
source  ~/Anaconda3-5.1.0/bin/activate tf

#
docker run -p 8888:8888 -p 6006:6006 -it --name="Anaconda-tensorflow" -v C:/Users/Administrator/tensorflow\Anaconda-tensorflow/TensorFlow-Tutorials:/root/notebook daxiang6506/anaconda-tensorflow

#必须使用这个版本，默认版本不行
pip install bleach==1.5.0

jupyter notebook --ip=* --allow-root --port=8888
tensorboard --logdir=/root/notebook/tb-log

#为了使用opencv，需要安装这些包，之后安装相应的python包，jupytor kernel重启的话，增加docker内存
apt-get update
apt-get install libgtk2.0-dev

pip install h5py
pip install opencv-python
pip install configobj
pip install keras
pip install Cython
```
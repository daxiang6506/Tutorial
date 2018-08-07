# Reinforcement Learning
## 案例
* [强化学习](https://github.com/Hvass-Labs/TensorFlow-Tutorials/blob/master/16_Reinforcement_Learning.ipynb)

## 参考
* [gym](https://github.com/openai/gym#installation)

## 环境搭建
* 下载代码
  ```
  git clone https://github.com/Hvass-Labs/TensorFlow-Tutorials.git
  ```
* 运行 `docker image`
  ```
  docker run -p 8888:8888 -p 6006:6006 -it --rm --name="tensorflow-anaconda3-rl" -v $(pwd):/root/notebook daxiang6506/tensorflow:anaconda3-1.0.4 /bin/bash
  ```
  ```
  docker run -p 8888:8888 -p 6006:6006 -it --restart=always --name="tensorflow-anaconda3-rl" -v $(pwd):/root/notebook daxiang6506/tensorflow:anaconda3-1.0.4 /bin/bashß
  ```
* 下载并安装 `gym`
  ```
  git clone https://github.com/openai/gym.git
  cd gym
  pip install -e '.[all]'
  ```

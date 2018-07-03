# Tensorflow Serving
* 有了模型之后我们还要将其做成产品，Tensorflow提供了Tensorflow Serving，可以将训练的模型直接做成一个rpc服务，外部可以通过调用rpc来获取模型输出结果。
## 参考
* [利用Docker和阿里云容器服务轻松搭建TensorFlow Serving集群](https://yq.aliyun.com/articles/60894)
* [Using TensorFlow Serving via Docker](https://www.tensorflow.org/serving/docker
)
## 命令
* bitnami
  ```
  docker run -it -p 5000:9000 -v /home/tf/servering/model_name:/bitnami/model-data bitnami/tensorflow-serving
  ```
## Code
* 源码安装
  ```
  FROM ubuntu:16.04

  MAINTAINER Jeremiah Harmsen <jeremiah@google.com>
  
  RUN apt-get update && apt-get install -y \
          build-essential \
          curl \
          git \
          libfreetype6-dev \
          libpng12-dev \
          libzmq3-dev \
          mlocate \
          pkg-config \
          python-dev \
          python-numpy \
          python-pip \
          software-properties-common \
          swig \
          zip \
          zlib1g-dev \
          libcurl3-dev \
          openjdk-8-jdk\
          openjdk-8-jre-headless \
          wget \
          && \
      apt-get clean && \
      rm -rf /var/lib/apt/lists/*
  
  # Set up grpc
  
  RUN pip install mock grpcio
  
  # Set up Bazel.
  
  ENV BAZELRC /root/.bazelrc
  # Install the most recent bazel release.
  ENV BAZEL_VERSION 0.5.4
  WORKDIR /
  RUN mkdir /bazel && \
      cd /bazel && \
      curl -fSsL -O https://github.com/bazelbuild/bazel/releases/download/$BAZEL_VERSION/bazel-$BAZEL_VERSION-installer-linux-x86_64.sh && \
      curl -fSsL -o /bazel/LICENSE.txt https://raw.githubusercontent.com/bazelbuild/bazel/master/LICENSE && \
      chmod +x bazel-*.sh && \
      ./bazel-$BAZEL_VERSION-installer-linux-x86_64.sh && \
      cd / && \
      rm -f /bazel/bazel-$BAZEL_VERSION-installer-linux-x86_64.sh
  
  CMD ["/bin/bash"]
  ```
  >The Tensorflow Serving Python API is only published for Python 2, but will work for Python 3 if you either build it yourself, or download the Python 2 version, unzip it, and copy it into your Python 3 path. There is a feature request to publish the Python 3 package as well.

  >Binaries are placed in the bazel-bin directory, and can be run using a command like:  
  `bazel-bin/tensorflow_serving/model_servers/tensorflow_model_server`

## bitnami/tensorflow-serving
* /opt/bitnami/tensorflow-serving/bin/tensorflow-serving.sh
  ```
  #!/bin/bash
  
  usage="$(basename "$0") [--help] [start|start-foreground|stop|status] -- Wrapper to start the tensorflow service"
  
  is_tensorflow_serving_running() {
      PID=''
      RUNNING=0
      if [ -f "/opt/bitnami/tensorflow-serving/tmp/tensorflow-serving.pid" ]; then
          PID=$(cat "/opt/bitnami/tensorflow-serving/tmp/tensorflow-serving.pid")
      fi
      if [ -n "${PID}" ] && kill -0 $PID 2>/dev/null ; then
          RUNNING=1
      else
          RUNNING=0
      fi
      return $RUNNING
  }
  
  case "$1" in
      --help)
          echo "$usage"
          exit
          ;;
      start)
          is_tensorflow_serving_running
          RUNNING=$?
          if [ $RUNNING -eq 0 ]; then
              echo "TensorFlow Serving is not running... starting server in background mode"
              tensorflow_model_server --port=9000 --model_config_file="/opt/bitnami/tensorflow-serving/conf/tensorflow-serving.conf" --file_system_poll_wait_seconds=5 > "/opt/bitnami/tensorflow-serving/logs/tensorflow-serving.log" 2>&1 &
              echo $! > "/opt/bitnami/tensorflow-serving/tmp/tensorflow-serving.pid"
          else
              echo "TensorFlow Serving is already running"
          fi
          ;;
      start-foreground)
          is_tensorflow_serving_running
          RUNNING=$?
          if [ $RUNNING -eq 0 ]; then
              echo "TensorFlow Serving is not running... starting server in foreground mode"
              tensorflow_model_server --port=9000 --model_config_file="/opt/bitnami/tensorflow-serving/conf/tensorflow-serving.conf" --file_system_poll_wait_seconds=5
          else
              echo "TensorFlow Serving is already running"
          fi
          ;;
      stop)
          if [ -f "/opt/bitnami/tensorflow-serving/tmp/tensorflow-serving.pid" ]; then
              echo "Stopping TensorFlow Serving"
              PID=$(cat "/opt/bitnami/tensorflow-serving/tmp/tensorflow-serving.pid")
              kill -0 $PID > /dev/null 2>&1
              if [ $? -eq 0 ]; then
                  kill -INT $PID
              fi
              rm "/opt/bitnami/tensorflow-serving/tmp/tensorflow-serving.pid"
          else
              echo "TensorFlow Serving is not running"
          fi
          ;;
      status)
          is_tensorflow_serving_running
          RUNNING=$?
          if [ $RUNNING -eq 0 ]; then
              echo "TensorFlow Serving is not running"
          else
              echo "TensorFlow Serving is running"
          fi
          ;;
      *)
          echo "echo $usage"
          exit 1
          ;;
  esac
  ```
  >tensorflow_model_server --port=9000 
* bitnami-docker-tensorflow-serving/0/rootfs/run.sh
  ```
  #!/bin/bash
  . /opt/bitnami/base/functions
  . /opt/bitnami/base/helpers
  
  TENSORFLOW_SERVING_HOME="/opt/bitnami/tensorflow-serving"
  USER=tensorflow
  
  info "Starting ${DAEMON}..."
  exec gosu ${USER} bash -c "${TENSORFLOW_SERVING_HOME}/bin/tensorflow-serving.sh start && tail -f ${TENSORFLOW_SERVING_HOME}/logs/tensorflow-serving.log"
  ```
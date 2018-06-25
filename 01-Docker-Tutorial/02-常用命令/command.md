## 常用命令
* docker images
  ```
  docker images --filter "dangling=true"
  docker images --format "table {{.ID}}\t{{.Repository}}"
  docker images -f "label=Name=tensorflow-demo" -f "label=Version=0.0.1"
  ```
* docker run
  ```
  #not work
  docker run -d -p 80:80 my_image service nginx start
  #work
  docker run -d -p 80:80 my_image nginx -g 'daemon off;'

  docker run -d -it --name devtest -v "$(pwd)"/target:/app nginx:latest
  docker run --rm -P --name pg_test eg_postgresql
  docker run --rm -t -i --link pg_test:pg eg_postgresql bash
  docker run --rm --volumes-from pg_test -t -i busybox sh
  docker run --restart=always redis
  docker run -it --entrypoint /bin/bash example/redis
  docker run -it --entrypoint="" mysql bash
  docker run --name clj_mysql_3 -e MYSQL_ROOT_PASSWORD=123456  -d -p 33062:3306 clj_mysql:5.6.28 /entrypoint.sh mysqld
  docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer
  docker run -d --name topdemo ubuntu /usr/bin/top -b
  export today=Wednesday
  docker run -e "deep=purple" -e today --rm alpine env
  docker run --rm -e "foo=bar" microsoft/nanoserver cmd /s /c set
  ```
  >[关于/var/run/docker.sock](https://blog.csdn.net/fundebug/article/details/70213275)
* docker exec
  ```
  docker exec a1 ping a2
  docker exec lamp-test ps

  ```
* docker inspect
  ```
  docker inspect -f '{{.NetworkSettings.Networks.b1.IPAdress}}' a1
  docker inspect -f "{{ .RestartCount }}" my-container
  docker inspect -f '{{.HostConfig.LogConfig.Type}}' 053a1133a448
  ```
* docker build
  ```
  docker build .
  docker build github.com/creack/docker-firefox
  docker build - < Dockerfile
  docker build -t vieux/apache:2.0 .
  docker build -t whenry/fedora-jboss
  ```
* docker ps
  ```
  docker ps -l
  docker ps -a
  docker ps --format "table {{.ID}}\t {{.Image}}\t {{.Ports}}"
  ```
* docker diff
  ```
  docker diff 812a997f614a
  ```
* doccker commit
  ```
  docker commit 18878cd1d72a daxiang6506/tensorflow:Anaconda3-5.1.0-tf
  ```
* docker save/load
  ```
  docker save image_name > /home/save.tar
  docker load < /home/save.tar
  docker save -o images.tar postgres:9.6 mongo:3.4
  docker save -o ~/test.tar memcached:latest
  docker load -i ~/test.tar
  ```
* docker import/export
  ```
  docker export <CONTAINER ID >> my_container.tar
  docker export -o postgres-export.tar postgres
  docker import postgres-export.tar postgres:latest
  cat my_container.tar |docker import -image_name:tag
  ```
* docker attach
  ```
  docker attach topdemo
  ```
* docker top
  ```
  docker top lamp-test
  ```
* docker history
  ```
  docker history --format "table{{.CreatedBy}}\t{{.Size}}" --no-trunc 3b617986d375
  ```
* docker rm
  ```
  docker rm `docker ps -a -q`
  ```
* docker cp
  ```
  docker cp Name:/container_path to_path
  docker cp ID:/container_path to_path
  ```
* docker volume
  ```
  docker volume create my-vol
  docker volume ls
  docker volume inspect my-vol
  docker volume rm my-vol
  ```
* docker rm
  ```
  docker rm $(docker ps -q) -f
  ```
* docker rmi
  ```
  docker rmi $(docker images -f "dangling=true" -q)
  ```
* docker stats
  ```
  docker stats --all --format "table {{.Container}}\t{{.CPUPerc}}\t{{.MemUsage}}" fervent_panini
  ```
* docker attach
  ```
  docker attach --sig-proxy=false $Container_ID
  ```
  >要attach的容器必须正在运行，attach后可以通过Ctrl-C来detach，实际上是不一定的，除非运行的时候加了-i参数，如果container正在前台运行，如输出nginx的access.log日志，Ctrl-C不仅会退出容器，还会导致nginx停止，detach的意思应该是脱离容器终端，但容易依然运行，attch可以带上参数--sig-proxy=false来确保Ctrl-C不会关闭容器。
* docker tag
  ```
  $a=${REGPREFIX}+"discovery-server"
  docker tag $(docker build -t ${a} -q .) ${a}:$(Get-Date -Format 'yyyymmdd-HHmmss')
  ```
* docker stop/kill
  >[docker容器如何优雅的终止](https://www.jb51.net/article/96617.htm)
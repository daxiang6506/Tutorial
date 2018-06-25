## 安装
### CentOS
1. 查看操作系统版本  
   ```
   cat /etc/redhat-release

   ###CentOS Linux release 7.3.1611 (Core)
   ```  
2. 备份yum源
   ```
   mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
   ```
3. 下载新的CentOS-Base.repo 到/etc/yum.repos.d/ 
   > CentOS-Base.repo 是yum 网络源的配置文件
   ```
   wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
   ```
4. 运行yum makecache生成缓存
   ```
   yum clean all
   yum makecache
   ```
5. 安装 yum-utils,提供yum-config-manager 默认已经安装
   ```
   yum install -y yum-utils
   ```
6. 使用yum-config-manager安装repository
   ```
   yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
   yum makecache fast
   ```
7. 查询docker版本
   ```
   yum list docker-ce.x86_64 --showduplicates | sort -r

   ### docker-ce.x86_64  17.03.1.ce-1.el7.centos  docker-ce-stable
   ### docker-ce.x86_64  17.03.1.ce-1.el7.centos  docker-ce-stable
   ### docker-ce.x86_64  17.03.0.ce-1.el7.centos  docker-ce-stable
   ### Available Packages
   ```
8. 安装指定版本的Docker-CE: (VERSION 例如上面的 17.03.0.ce.1-1.el7.centos)
   ```
   yum -y install docker-ce-17.09.0.ce-1.el7.centos
   ```
9. 启动服务
   ```
   service docker start
   ```
10. 配置镜像仓库，配置本地仓库
    >docker daemon监听三种不同的套接字：unix, tcp, fd来处理docker client的请求，其中unix套接字表示仅支持主机自身的请求，tcp表示支持remote client, fd表示systemd socket 一般情况下systemd都以此工作。docker daemon的配置文件可以指定配置哪种监听方式，这三种方式可以同时存在。  
    [Docker Daemon连接方式详解](https://www.jianshu.com/p/7ba1a93e6de4)
    ```
    cp /lib/systemd/system/docker.service /etc/systemd/system/docker.service

    sed -i "s|ExecStart=/usr/bin/dockerd|ExecStart=/usr/bin/dockerd --registry-mirror=https://y7c8qy9p.mirror.aliyuncs.com/|g" /etc/systemd/system/docker.service

    sed -i "s|ExecStart=/usr/bin/dockerd|ExecStart=/usr/bin/dockerd --registry-mirror=https://y7c8qy9p.mirror.aliyuncs.com --insecure-registry=192.168.3.0/24|g" /etc/systemd/system/docker.service

    sed -i "s|ExecStart=/usr/bin/dockerd|ExecStart=/usr/bin/dockerd -H unix:///var/run/docker.sock -H tcp://0.0.0.0:2375 --registry-mirror=https://y7c8qy9p.mirror.aliyuncs.com --insecure-registry=192.168.3.0/24|g" /etc/systemd/system/docker.service
    ```
11. 查看docker运行状态/打开/关闭/重启docker服务/重新加载配置/重新启动
   ```
   sudo systemctl enable docker
   service docker status
   service docker start
   service docker stop
   service docker restart
   sudo systemctl daemon-reload
   sudo systemctl restart docker
   ```
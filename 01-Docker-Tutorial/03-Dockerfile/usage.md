## 常见语法
* RUN
  ```
  RUN /bin/bash -c 'source $HOME/.bashrc; \ 
          echo $HOME'
  ```
  >RUN是在Build时运行的，先于CMD和ENTRYPOINT。Build完成了，RUN也运行完成后，再运行CMD或者ENTRYPOINT
* ENTRYPOINT
  >ENTRYPONT和CMD的不同点在于执行 `docker run` 时参数传递方式，CMD指定的命令可以被 `docker run` 传递的命令覆盖，ENTRYPOINT不会被覆盖。
  ```
  ENTRYPOINT ["executable", "param1", "param2"] (like an exec, the preferred form)
  ENTRYPOINT command param1 param2 (as a shell)
  ```
  ```
  # CMD指令将不会被执行，只有ENTRYPOINT指令被执行
  CMD echo “Hello, World!”
  ENTRYPOINT ls -l
  ```
  >当独自使用时，如果你还使用了CMD命令且CMD是一个完整的可执行的命令，那么CMD指令和ENTRYPOINT会互相覆盖只有最后一个CMD或者ENTRYPOINT有效
  ```
  FROM ubuntu
  CMD ["-l"]
  ENTRYPOINT ["/usr/bin/ls"]
  ```
  >CMD指令配合使用来指定ENTRYPOINT的默认参数，这时CMD指令不是一个完整的可执行命令，仅仅是参数部份
* CMD
  ```
  CMD ["executable","param1","param2"] (like an exec, this is the preferred form)
  CMD command param1 param2 (as a shell)
  ```
  ```
  CMD ["param1","param2"] (as default parameters to ENTRYPOINT)
  ```
  >当Dockerfile指定了ENTRYPOINT，则使用第三种方式

## 参考
* [Dockerfile里指定执行命令用ENTRYPOING和用CMD有何不同？](https://segmentfault.com/q/1010000000417103)
* [Dockerfile创建自定义Docker镜像以及CMD与ENTRYPOINT指令的比较](http://www.cnblogs.com/lienhua34/p/5170335.html)
* [如何使用Dockerfile构建镜像](https://blog.csdn.net/we_shell/article/details/38445979)
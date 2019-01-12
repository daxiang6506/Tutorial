# Micro Service

## 参考

* [etcd是什么东西？它和ZooKeeper有什么区别？](http://dockone.io/question/7)
* [raft](http://thesecretlivesofdata.com/raft/)
* [开放分布式追踪（OpenTracing）入门与 Jaeger 实现](https://zhuanlan.zhihu.com/p/34318538?utm_source=com.alibaba.android.rimet&utm_medium=social)
  > * Logging - 用于记录离散的事件。例如，应用程序的调试信息或错误信息，它是我们诊断问题的依据。
  > * Metrics - 用于记录可聚合的数据。例如，队列的当前深度可被定义为一个度量值，在元素入队或出队时被更新。HTTP请求个数可被定义为一个计数器，新请求到来时进行累加。
  > * Tracing - 用于记录请求范围内的信息。例如，一次远程方法调用的执行过程和耗时，它是我们排查系统性能问题的利器。
  > * Zipkin 专注于 tracing 领域；Prometheus 开始专注于 metrics，随着时间推移可能会集成更多的 tracing 功能，但不太可能深入 logging 领域； ELK，阿里云日志服务这样的系统开始专注于 logging 领域，但同时也不断地集成其他领域的特性到系统中来，正向上图中的圆心靠近
  > * 分布式追踪系统发展很快，种类繁多，但核心步骤一般有三个：***代码埋点***，***数据存储***、***查询展示***
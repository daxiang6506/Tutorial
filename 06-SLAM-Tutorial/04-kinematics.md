# 动力学

## 资源

* [ESKF(error-state Kalman Filter)总结](https://blog.csdn.net/wubaobao1993/article/details/84327700)
  >状态变量为：[位移，姿态，速度，加速度的bias，角速度的bias]，即x=[p,q,v,ba,bg]

* [github:SLAM 学习与开发经验分享](https://github.com/GeekLiB/Lee-SLAM-source)
  >[SLAM的前世今生](https://www.leiphone.com/news/201605/5etiwlnkWnx7x0zb.html)

* [如何理解SLAM中的First-Estimates Jacobian？](https://www.zhihu.com/question/52869487)
  >Observability能观性
  >DOF自由度
  >Inconsistency的原因是，计算时采用了不同的线性化状态点。那么，用相同的状态点进行线性化计算就不会有这个问题了，具体来说，位姿采用propagated值而非updated值，landmark使用第一次估计值。First Estimate就是这个直观含义，即采用estimation from the first time。这样，虽然线性化点离真值的误差可能相对更大，但能保证能观性矩阵的性质和“理想”系统一样

* [SLAM中的marginalization 和 Schur complement](https://blog.csdn.net/heyijia0327/article/details/52822104)

* [如何通俗并尽可能详细解释卡尔曼滤波？](https://www.zhihu.com/question/23971601/answer/137325095)
  >the great success of the Kalman filter is due to its small computational requirement, elegant recursive properties, and its status as the optimal estimator for one-dimensional linear systems with Gaussian error statistics

* [自动驾驶的挑战和发展](https://zhuanlan.zhihu.com/c_1071103636175765504)


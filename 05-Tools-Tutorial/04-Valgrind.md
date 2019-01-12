# VALGIND

## 工具

* [kcachegrind](http://kcachegrind.sourceforge.net/html/Home.html)
  >Callgrind uses runtime instrumentation via the Valgrind framework for its cache simulation and call-graph generation
  >源码安装失败
  >sudo apt-get install kcachegrind

## 参考

* [应用 Valgrind 发现 Linux 程序的内存问题](https://www.ibm.com/developerworks/cn/linux/l-cn-valgrind/index.html)
* [内存调试技巧](https://www.ibm.com/developerworks/cn/aix/library/au-memorytechniques.html)
* [如何在linux下检测内存泄漏](https://www.ibm.com/developerworks/cn/linux/l-mleak/)
* [解释“Conditional jump or move depends on uninitialised value(s)”](https://www.sharcnet.ca/help/index.php/VALGRIND)
* [valgrind的callgrind工具进行多线程性能分析](https://www.cnblogs.com/zengkefu/p/5642991.html)

## 安装

* [valgrind安装与使用](https://www.cnblogs.com/defen/p/5560926.html)
* [valgrind](http://www.valgrind.org/)
  >`sudo apt-get install valgrind`  
  >[Linux下性能分析工具和内存泄露检测工具的简介](https://blog.csdn.net/u014717036/article/details/50762252)
  >`valgrind --log-file=./valgrind_report_all --tool=memcheck --leak-check=full --show-leak-kinds=all ./pose_estimation_3d2d 1.png 2.png 1_depth.png 2_depth.png`

## 命令

* valgrind 3.13 supported xtree
* ```bash
  valgrind --tool=drd --show-stack-usage=<yes|no> [default: no]
  ```

* ```bash
  valgrind --tool=helgrind --read-var-info=yes ./octomap_mapping
  ```
* 内存泄漏输出文件到`kcachegrind`
  ```
  valgrind --leak-check=full --show-leak-kinds=all --xtree-leak=yes --xtree-leak-file=xtleak.kcg --tool=memcheck ./octomap_mapping
  ```
* 内存泄漏检查详细指标
  ```
   valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes --log-file=suppression5.txt --tool=memcheck ./octomap_mapping
  ```
* To see information on the sources of uninitialised data in your program
  ```
  valgrind --track-origins=yes --log-file=suppression3.txt --tool=memcheck ./octomap_mapping
  ```
* 生成xtree
  ```
  valgrind --xtree-memory=full --xtree-memory-file=xtmemory.kcg ./octomap_mapping
  ```
* 生成suppression list 
  ```
  valgrind --log-file=suppression-log.txt --gen-suppressions=all ./octomap_mapping
  ```
* 将suppression list 保存为file.supp
* 抑制不需要的错误，-v选项可以看到抑制了哪些
  ```
  valgrind  --suppressions=/path/to/file.supp -v --log-file=log.txt ./octomap_mapping
  >this tells Valgrind to print out a suppression for each reported error, which you can then copy into a suppressions file.
  ```
  --read-inline-info=yes
  ```
  >
* So the best solution is to turn off optimisation altogether.Since this often makes things unmanageably slow, a reasonable compromise is to use ****-O****

* Also, you should compile your code with -Wall because it can identify some or all of the problems that Valgrind can miss at the higher optimisation levels.

* A second -v gives yet more detail.if you want to know how many times each error occurred, run with the -v option

* In general, you should try and fix errors in the order that they are reported

* The error-checking tools detect numerous problems in the system libraries, such as the C library, which come pre-installed with your OS. You can't easily fix these, but you don't want to see these errors (and yes, there are many!) So Valgrind reads a list of errors to suppress at startup. A default suppression file is created by the ./configure script when the system is built.

* The GNU C library (libc.so), which is used by all programs, may allocate memory for its own uses. Usually it doesn't bother to free that memory when the program ends—there would be no point, since the Linux kernel reclaims all process resources when a process exits anyway, so it would just slow things down.

* The GNU Standard C++ library (libstdc++.so), which is used by all C++ programs compiled with g++, may allocate memory for its own uses. Usually it doesn't bother to free that memory when the program ends—there would be no point, since the kernel reclaims all process resources when a process exits anyway, so it would just slow things down.

* The main thing to point out with respect to threaded programs is that your program will use the native threading library, but Valgrind serialises execution so that only one (kernel) thread is running at a time. This approach avoids the horrible implementation problems of implementing a truly multithreaded version of Valgrind, but it does mean that threaded apps never use more than one CPU simultaneously, even if you have a multiprocessor or multicore machine.

* This difference in scheduling may cause your program to behave differently, if you have some kind of concurrency, critical race, locking, or similar, bugs. In that case you might consider using the tools Helgrind and/or DRD to track them down.

* Valgrind's use of thread serialisation implies that only one thread at a time may run. On a multiprocessor/multicore system, the running thread is assigned to one of the CPUs by the OS kernel scheduler. When a thread acquires the lock, sometimes the thread will be assigned to the same CPU as the thread that just released the lock. Sometimes, the thread will be assigned to another CPU. When using pipe based locking, the thread that just acquired the lock will usually be scheduled on the same CPU as the thread that just released the lock. With the futex based mechanism, the thread that just acquired the lock will more often be scheduled on another CPU.

* Valgrind's thread serialisation and CPU assignment by the OS kernel scheduler can interact badly with the CPU frequency scaling available on many modern CPUs. To decrease power consumption, the frequency of a CPU or core is automatically decreased if the CPU/core has not been used recently. If the OS kernel often assigns the thread which just acquired the lock to another CPU/core, it is quite likely that this CPU/core is currently at a low frequency. The frequency of this CPU will be increased after some time. However, during this time, the (only) running thread will have run at the low frequency. Once this thread has run for some time, it will release the lock. Another thread will acquire this lock, and might be scheduled again on another CPU whose clock frequency was decreased in the meantime.

* The futex based locking causes threads to change CPUs/cores more often. So, if CPU frequency scaling is activated, the futex based locking might decrease significantly the performance of a multithreaded app running under Valgrind. Performance losses of up to 50% degradation have been observed, as compared to running on a machine for which CPU frequency scaling has been disabled. The pipe based locking locking scheme also interacts badly with CPU frequency scaling, with performance losses in the range 10..20% having been observed.

* To avoid such performance degradation, you should indicate to the kernel that all CPUs/cores should always run at maximum clock speed. Depending on your Linux distribution, CPU frequency scaling may be controlled using a graphical interface or using command line such as ****cpufreq-selector**** or ****cpufreq-set****.

* An alternative way to avoid these problems is to tell the OS scheduler to tie a Valgrind process to a specific (fixed) CPU using the ****taskset**** command. This should ensure that the selected CPU does not fall below its maximum frequency setting so long as any thread of the program has work to do.

* In C++ it's important to deallocate memory in a way compatible with how it was allocated. The deal is:

If allocated with malloc, calloc, realloc, valloc or memalign, you must deallocate with free.

If allocated with new, you must deallocate with delete.

If allocated with new[], you must deallocate with delete[].

* Cycles are not bad in itself, but tend to make performance analysis of your code harder. This is because inclusive costs for calls inside of a cycle are meaningless. The definition of inclusive cost, i.e. self cost of a function plus inclusive cost of its callees, needs a topological order among functions. For cycles, this does not hold true: callees of a function in a cycle include the function itself. Therefore, KCachegrind does cycle detection and skips visualization of any inclusive cost for calls inside of cycles. Further, all functions in a cycle are collapsed into artificial functions called like Cycle 1

Misuses of the POSIX pthreads API.

Potential deadlocks arising from lock ordering problems.

Data races -- accessing memory without adequate locking or synchronisation.
是一个用来可视化Callgrind结果的工具。
GNU General Public License
Execution TreesCachegrinds
Cachegrind
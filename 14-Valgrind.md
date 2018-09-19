* [应用 Valgrind 发现 Linux 程序的内存问题](https://www.ibm.com/developerworks/cn/linux/l-cn-valgrind/index.html)
* [内存调试技巧](https://www.ibm.com/developerworks/cn/aix/library/au-memorytechniques.html)
* [如何在linux下检测内存泄漏](https://www.ibm.com/developerworks/cn/linux/l-mleak/)
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
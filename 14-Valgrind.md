* [应用 Valgrind 发现 Linux 程序的内存问题](https://www.ibm.com/developerworks/cn/linux/l-cn-valgrind/index.html)
* [内存调试技巧](https://www.ibm.com/developerworks/cn/aix/library/au-memorytechniques.html)
* [如何在linux下检测内存泄漏](https://www.ibm.com/developerworks/cn/linux/l-mleak/)

* ```
  valgrind --gen-suppressions=yes ./octomap_mapping
  ```
  >this tells Valgrind to print out a suppression for each reported error, which you can then copy into a suppressions file.
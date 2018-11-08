## 资源
* [glogg](http://glogg.bonnefon.org/)
  >日志工具
* [incredibuild](https://www.incredibuild.com/)
  >分布式编译
* [distributed builds for C, C++ and Objective C](https://github.com/distcc/distcc)
  >http://manpages.ubuntu.com/manpages/trusty/en/man1/distccd.1.html
* [现代 C++ 开发(1)：线程安全注解](https://zhuanlan.zhihu.com/p/47837673)
* [有哪些GitHub项目的README堪称教科书](https://www.zhihu.com/question/299390628/answer/515174697)
* [c++有什么好的协程支持的易用的高并发库吗](https://www.zhihu.com/question/36150312/answer/500180866)
* [linux下的高效代码搜索工具-ack](https://blog.csdn.net/kevinx_xu/article/details/20470903)
* [The Definitive C++ Book Guide and List](https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list)
  >C++ Concurrency In Action 
  >>锁与无锁设计   
  >>流水线设计  

  >Effective_Modern_C++  
  >More Effective C++中文版  
* [Heterogeneous Computing with OpenCL 2.0](https://chenxiaowei.gitbooks.io/heterogeneous-computing-with-opencl2-0/content/)  
  >GPU体系结构
* [Manage memory efficiently in your C++ code with
smart pointers](https://indico.cern.ch/event/666222/contributions/2722821/attachments/1552323/2439274/Pointers_SAiola.pdf)
* [在线编译](http://coliru.stacked-crooked.com/)
  >g++-4.9 -std=c++11 -O2 -Wall -pedantic -pthread main.cpp && ./a.out
* [A garbage collector for C and C++](https://www.hboehm.info/gc/)
* [awesome-cpp](https://github.com/fffaraz/awesome-cpp?utm_source=wechat_session&utm_medium=social&utm_oi=568910917765632000#frameworks)
* [Software optimization resources](https://www.agner.org/optimize/)
  >Test programs for measuring clock cycles and performance monitoring
* [TOOL:relacy](http://www.1024cores.net/home/lock-free-algorithms/introduction)
* [How to Design Programs, Second Edition](https://htdp.org/2018-01-06/Book/)
* [性能测试工具VTune的功能和用法介绍](https://blog.csdn.net/WY_stutdy/article/details/79106501)
* [CodeXL](https://gpuopen.com/codexl-2-6-released/)
* [ubuntu14.04安装doxygen](https://blog.csdn.net/qq632544991p/article/details/46642145)
  >sudo apt-get install graphviz
* [强大的Doxygen工具使用手册](https://blog.csdn.net/leehong2005/article/details/9137889?utm_source=blogxgwz1)
* [Ubuntu使用doxygen将源码生成调用关系图](https://blog.csdn.net/ZeroLiko/article/details/78162408)
* [绘制函数调用图（call graph）（4）：doxygen + graphviz](https://blog.csdn.net/benkaoya/article/details/79763668)
## tips
* [ubuntu下使用CPU频率控制](https://blog.csdn.net/sunnypotter/article/details/18506727?utm_source=blogxgwz0)

## 建立环境
* [指导书](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Manual+Page+of+Localization+Refactor+May+31th+2018&spaceKey=RRT)

* [How to download dependency repository artifacts?](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=51676609)

* [Jfrog CMD Installation & Usage](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=42537772)

* [安装opencl](https://confluence.ygomi.com:8443/display/RRT/How+to+Set+Up+OpenCL+Compilation+Environment+for+FindOpenCL.cmake+in+CMake3.5)

* [Introduce sysStar tool](https://confluence.ygomi.com:8443/pages/viewpage.action?title=Introduce+sysStar+tool&spaceKey=RRT)

* [Install Docker in Ubuntu](https://confluence.ygomi.com:8443/display/RDC/Install+Docker+in+Ubuntu)
## 虚拟机环境（最终环境没有建好，algorithm_common编译不过，可以通过jfog拉编好的库来规避）
* 安装库
  >```
  >sudo apt-get install libusb-1.0-0-dev
  >sudo apt-get install libudev-dev
  >sudo apt-get install libpcap-dev
  >```
* 编译core/common出错
  >```
  >#解决办法：
  >cp rdb-tools/core/common/thirdParty/eigen/cmake/FindEigen3.cmake  /usr/local/share/cmake-3.5/Modules/
  >```
* 解决db版本问题
  >```
  >#拷贝这两个文件到指定目录下（标哥提供，适配old db版本）
  >SectionMapDef.h
  >SnippetDef.h
  >core/algorithm_common/dist/x64/include
  >#然后重新编译（要用到dist下的include文件）
  >core/algorithm_vehicle_localization

## docker环境
* 命令
  >```
  >docker run -it --name master-build -v "${PWD}":/data -w /data dockerhub.ygomi.com/rdb:latest bash
  >```
* 解决依赖问题
  >```
  ># 需要重新编译data-receiver
  >git clone ssh://git@stash.ygomi.com:7999/as/data-receiver.git
  ># 编译data-receiver需要rdb-device-base-rules（由标哥提供）
  >framework/device/rdb-device-base-rules
  >```
* 解决db版本问题
  >```
  >#拷贝这两个文件到指定目录下（标哥提供，适配old db版本）
  >SectionMapDef.h
  >SnippetDef.h
  >core/algorithm_common/dist/x64/include
  >#然后重新编译（要用到dist下的include文件）
  >core/algorithm_vehicle_localization

## linux
* [linux中的ldd命令简介](https://blog.csdn.net/stpeace/article/details/47069215)

## C++
* [析构函数是否必须为虚函数？什么情况下才应该定义析构函数为虚函数？](https://blog.csdn.net/zhangqk2016/article/details/51849535)
* [C/C++中#pragma once的使用](https://blog.csdn.net/fengbingchun/article/details/78696814)
* [C++ 中using 的使用](https://blog.csdn.net/shift_wwx/article/details/78742459)
  >using value_type = _Ty;
* [cpp类声明 定义 实现](https://blog.csdn.net/mardax/article/details/54948173)
  >类申明只能使用指针引用类型
  >类定义才能使用成员函数（只定义类，不定义成员函数）
* [声明并定义相同类](https://blog.csdn.net/eclipser1987/article/details/7516968)
  >不会报错，会替代，造成问题
* [为什么类的定义应当写在头文件中,从而被多个源文件包含](https://blog.csdn.net/baoxiaofeicsdn/article/details/48338515)
  >如果对同一个类的两个定义完全相同且出现在不同编译单位，会被当作同一个定义
  >定义了类，但是类的实现在其他位置，编译时，编译器不会去找类的实现，链接时编译器才会去寻找这个类的实现
* [c++编译过程简述](https://blog.csdn.net/fl2_pigy/article/details/80640352)
  >内部链接的符号不能在别的编译单元中使用。但不同的编译单元可以拥有同样的名称的符号
* [头文件中写类的实现出现函数重复定义的问题](https://blog.csdn.net/dengm155/article/details/51692285)
  >inline函数,class和模板类函数被多次包含的情况下，编译器会自动把他们认为是同一个函数，不会发生二次定义的问题。前提是他们一模一样
* [C/C++: 强符号、弱符号与链接](http://blog.sina.com.cn/s/blog_6e32babb0102v0p9.html)
  >成员函数定义在头文件中的时候,不会导致链接问题(头文件被多个.cpp include, 每个cpp都调用到了这个成员函数,那么相应的每个.o 里都有这个成员函数的二进制代码, link完成后,肯定只能剩下一份, 那么这有好几份,岂不冲突! 正是由于这个强弱性, 所以才没事.)
* [理解C++的链接：C++内链接与外链接的意义](https://blog.csdn.net/u012999985/article/details/50429769)
  >外部链接就是让各个.cpp文件能链接到一起，在.cpp文件遇到第一个{}之前，他们的作用域是相同的，拥有外部链接的实体（全局函数，变量等）出现在第一个{}之前，而且名字相同，就是定义重复的错误。
  >如果是想static int a = 2;这样的定义就会在所有包含他的.cpp文件中生成一个副本，如果被大量源文件include的话，就会占据大量的空间，造成内存浪费
* [C++中的static关键字 ，外部链接性,内部链接性和无链接性](https://blog.csdn.net/Fire_Sky_Ho/article/details/75303180)
* [C++之 未命名的名字空间](http://blog.sina.com.cn/s/blog_6ba7867b01016pha.html)
  >解决static全局函数问题
* [函数实现不放在头文件的原因，及何时可以放头文件的情况](https://blog.csdn.net/freeboy1015/article/details/8075849)
  >解决C++ 中全局函数的头文件复用问题
* [c++的编译过程](https://blog.csdn.net/ferrari_hong/article/details/79629468)
  >头文件中可以写const对象的定义
  >头文件中可 以写内联函数（inline）的定义
  >头文件中可以写类 （class）的定义
  >这三个例外中的语法元素虽然“可以定义在多个源文件中”，但是“在一个源文件中只能出现一次”
  >条件编译#ifndef...#endif
  >#pragma once
* [深入理解C++中的explicit关键字](https://blog.csdn.net/kezunhai/article/details/38417087)
* [c++构造函数成员初始化中赋值和初始化列表两种方式的区别](https://www.cnblogs.com/simplepaul/p/7635648.html)
* [C++中struct和class的区别](https://www.cnblogs.com/ccsccs/articles/4025215.html)
* [C++中模板使用详解](https://www.cnblogs.com/sevenyuan/p/3154346.html)
  >模版可以分为两类，一个是函数模版，另外一个是类模版
* [关于C++域作用符详解](https://blog.csdn.net/Bruce_0712/article/details/53955887)
* [C和C++中的名字空间和作用域](https://www.cnblogs.com/qingergege/p/7512421.html)
* [C++typedef的详细用法](https://blog.csdn.net/hai008007/article/details/80651886)
* [C++命名空间namespace的使用规范](https://blog.csdn.net/wsx199397/article/details/52490300)
* [ADL with typedefs from another namespace](https://stackoverflow.com/questions/4155450/adl-with-typedefs-from-another-namespace)
* [typedef resolution across namespaces](https://stackoverflow.com/questions/5035504/typedef-resolution-across-namespaces)
* [Namespaces | Understanding C++ Program Structure](http://www.informit.com/articles/article.aspx?p=31783&seqNum=6)
  >using声明相当于把指定名字空间中的特定成员直接定义到当前作用域中
  >Using指示相当于增加指定名字空间作为符号查找域
* [C++基础知识和基本语法](https://confluence.ygomi.com:8443/pages/viewpage.action?pageId=50495783#C++%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E5%92%8C%E5%9F%BA%E6%9C%AC%E8%AF%AD%E6%B3%95%E4%B8%B2%E8%AE%B2-1.5GCC%E7%BC%96%E8%AF%91%E8%BF%87%E7%A8%8B)
  >在C++11中，右值由两个概念构成

  >一个是将亡值（xvalue，expiring value），将亡值时C++11新增的，与右值引用相关的表达式，比如，将要被移到的对象、T&&函数返回值、std::move返回值和转换为 T&&的类型的转换函数的返回值; 
  
  >另一个则是纯右值（prvalue，pure rvalue），比如，非引用返回的临时变量、运算表达式产生的临时变量、原始字面量和lambda表达式等都是纯右值。
* [c++ shared_ptr使用的几点注意](https://blog.csdn.net/man_sion/article/details/77196766)
* [关于Vector的size_type的问题的探讨 C++](https://blog.csdn.net/lkkb24/article/details/6948577)
* [c++11 多线程（3）atomic 总结](https://www.jianshu.com/p/8c1bb012d5f8)
* [C++ 输入/输出运算符重载](http://www.runoob.com/cplusplus/input-output-operators-overloading.html)
* [C++构造函数的default和delete](https://blog.csdn.net/u010591680/article/details/71101737)
* [C++11 std::unique_lock与std::lock_guard区别及多线程应用实例](https://blog.csdn.net/tgxallen/article/details/73522233)
* [（C++）关于i++和i++的左值、右值问题](https://www.cnblogs.com/AndyJee/p/4550457.html)
* [C++ 函数声明后面的const用法](https://blog.csdn.net/u013270326/article/details/78388305?utm_source=blogxgwz0)
* [const and global](https://stackoverflow.com/questions/9032475/const-and-global)
  >By default Linkage is external for non-const symbols and static (internal) for const symbols
* [C++中const、volatile、mutable的用法](https://www.cnblogs.com/xkfz007/articles/2419540.html)
* [C++智能指针](https://www.cnblogs.com/diysoul/p/5930396.html)
* [Solution: Smart Pointer Parameters](https://herbsutter.com/2013/06/05/gotw-91-solution-smart-pointer-parameters/)
* [Should we pass a shared_ptr by reference or by value?](https://stackoverflow.com/questions/3310737/should-we-pass-a-shared-ptr-by-reference-or-by-value)
* [C++11 thread-safe queue](https://stackoverflow.com/questions/15278343/c11-thread-safe-queue)
* [Implementing a Thread-Safe Queue using Condition Variables](https://www.justsoftwaresolutions.co.uk/threading/implementing-a-thread-safe-queue-using-condition-variables.html)
* [std::condition_variable::wait_for](https://en.cppreference.com/w/cpp/thread/condition_variable/wait_for)
  >```
  >return wait_until(lock, std::chrono::steady_clock::now() + rel_time, std::move(pred));. This overload may be used to ignore spurious awakenings
  >```
* [TOOL:relacy](http://www.1024cores.net/home/lock-free-algorithms/introduction)
  >****Wait-freedom**** means that each thread moves forward regardless of external factors like contention from other threads, other thread blocking  
  >
  >****Lock-freedom**** means that a system as a whole moves forward regardless of anything. Forward progress for each individual thread is not guaranteed (that is, individual threads can starve).  
  >
  >****Obstruction-freedom**** guarantee means that a thread makes forward progress only if it does not encounter contention from other threads  
  >
  >Waitfree, lockfree and obstruction-free algorithms provide a guarantee of ****termination-safety****  
  >
  >****Blocking Algorithms**** It's the weakest guarantee - basically all bets are off, the system as a whole may not make any forward progress. A blocked/interrupted/terminated thread may prevent system-wide forward progress infinitely. Mutex-based algorithms are also amenable to deadlocks, and a deadlocked system clearly makes no forward progress.
* [Memory Reordering/Memory Model 及其对.NET的影响](http://www.cnblogs.com/sun/archive/2010/02/03/1663064.html#2001829)
* [C++11的6种内存序总结](https://blog.csdn.net/lvdan1/article/details/54098559)
* [A Fast General Purpose Lock-Free Queue for C++](http://moodycamel.com/blog/2014/a-fast-general-purpose-lock-free-queue-for-c++)
  >[github](https://github.com/cameron314/concurrentqueue)
* [A Fast Lock-Free Queue for C++](http://moodycamel.com/blog/2013/a-fast-lock-free-queue-for-c++)
  >[github](https://github.com/cameron314/readerwriterqueue)
* [An Introduction to Lock-Free Programming](https://preshing.com/20120612/an-introduction-to-lock-free-programming/)
  >多线程，访问共享内存，线程之间不互相阻塞---lock free 编程
* [C++ new分配内存时的std::bad_alloc异常处理](https://blog.csdn.net/yanggaoqiang2013/article/details/38751313?utm_source=blogxgwz2)
* [C++ lambda表达式与函数对象](https://www.jianshu.com/p/d686ad9de817)
* [Trying to use lambda functions as predicate for condition_variable wait method](https://stackoverflow.com/questions/24345272/trying-to-use-lambda-functions-as-predicate-for-condition-variable-wait-method)
* [C++使用虚函数的时候，子类也要使用virtual关键字吗](https://blog.csdn.net/gao1440156051/article/details/45670715?utm_source=blogxgwz0)
* [C++ stringstream介绍，使用方法与例子](https://blog.csdn.net/joeblackzqq/article/details/7032703)
* [static_cast、dynamic_cast reinterpret_cast和const_](http://blog.sina.com.cn/s/blog_4a84e45b0100f57m.html)
* [使用ifstream和getline读取文件内容[c++]](https://www.cnblogs.com/JCSU/articles/1190685.html)
* [Slippy map tilenames](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames)
* [C++ 风格指南](https://zh-google-styleguide.readthedocs.io/en/latest/google-cpp-styleguide/contents/)
* [C++11 理解 (十八) 之 字串字面值](https://blog.csdn.net/y_xianjun/article/details/10228435?utm_source=blogxgwz2)
* [C++ | boost库 类的序列化](https://www.cnblogs.com/feixiao5566/p/5189246.html)
* [C++中string::npos的一些用法总结](https://blog.csdn.net/JIEJINQUANIL/article/details/51789682)
* [setprecision、fixed、showpoint的用法总结](https://blog.csdn.net/u011321546/article/details/9293547)
* [Limiting execution to certain CPUs](http://www.gnu.org/software/libc/manual/html_node/CPU-Affinity.html)
* [Pthread affinity before create threads](https://stackoverflow.com/questions/25472441/pthread-affinity-before-create-threads)
* [Linux CPU数、物理核、逻辑核的查看方法及线程进程的绑定方法](https://www.linuxidc.com/Linux/2018-07/153190.htm)
  >在top命令下，点击"1"可以查看各个逻辑核的占用情况
* [[ubuntu] cpu hotplugging](https://ubuntuforums.org/archive/index.php/t-1074167.html)
* [Can you use thread local variables inside a class or structure](https://stackoverflow.com/questions/10999131/can-you-use-thread-local-variables-inside-a-class-or-structure)
  >Thread-local storage applies to static variables only. There is no point in making non-static structure or class members thread-local.
* [struct和typedef struct](https://www.cnblogs.com/qyaizs/articles/2039101.html)
  >注意在C和C++里不同
* [C++ typedef typename 作用](https://blog.csdn.net/zhangxiao93/article/details/50569924)
* [typename在C++中的用法](https://www.cnblogs.com/wuchanming/p/3765345.html)
* [C++ 标准库之typeid](https://blog.csdn.net/xuqingict/article/details/25003713?utm_source=blogxgwz0)
* [C++学习 std:multimap介绍](https://blog.csdn.net/skdkjzz/article/details/43456225)
* [https://stackoverflow.com/questions/8341395/what-is-a-subnormal-floating-point-number](https://stackoverflow.com/questions/8341395/what-is-a-subnormal-floating-point-number)
* [Position Independent Code (PIC) in shared libraries](https://blog.csdn.net/astrotycoon/article/details/8456453)
* [What's the difference between cerr and cout in C++?](https://www.quora.com/Whats-the-difference-between-cerr-and-cout-in-C++)
  >0, 1, 2...9 are file descriptors in bash. 
  > 
  >0 stands for stdin, 1 stands for stdout, 2 stands for stderror. 3~9 is spare for any other temporary usage.  
  >
  >Any file descriptor can be redirected to other file descriptor or file by using operator > or >>(append).
* [I/O Redirection](http://www.tldp.org/LDP/abs/html/io-redirection.html)
* [第一个gtest程序（Linux）](https://www.jianshu.com/p/778f835cc18c)
* [C++ Type traits](https://www.boost.org/doc/libs/1_31_0/libs/type_traits/c++_type_traits.htm)
* [c++中 T C::* 是什么类型](https://www.zhihu.com/question/57905739)
* [C++11容器中新增加的emplace相关函数的使用](https://blog.csdn.net/fengbingchun/article/details/78670376?utm_source=blogxgwz4)
* [C++中std::allocator的使用](https://blog.csdn.net/fengbingchun/article/details/78943527)
* [Declaring variables inside loops, good practice or bad practice?](https://stackoverflow.com/questions/7959573/declaring-variables-inside-loops-good-practice-or-bad-practice)
  >The variable is not supposed to retain its value between each loop. In such case, you may need to initialize it every time.
* [C++11中变量初始化方法汇总](https://blog.csdn.net/q1302182594/article/details/47423347)
  >列表初始化 c++11 only  
  >拷贝初始化  
  >直接初始化  
  >默认初始化
  >参考资料[1]P236指出，类通过一个特殊的构造函数来控制默认初始化过程，这个类叫做默认构造函数。默认构造函数无需任何实参。参考资料[1]P637也指出，每个类各自定义其初始化对象的方式（默认构造函数）。例如，std::string，不管是定义于局部还是全局，都会默认初始化为空。  
  >类的初始化，定义不管带不带括号都调用默认构造方法
* [c++ declaration and initialization variables inside while loops](https://stackoverflow.com/questions/42534977/c-declaration-and-initialization-variables-inside-while-loops)
* [C++ Constructors and Memory Leaks](http://jsteemann.github.io/blog/2015/11/18/on-exception-handling/)
  >智能指针作为成员变量可以不用在析构函数里调用 delete
* [Destructors (C++)](https://msdn.microsoft.com/en-us/library/6t4fe76c.aspx)
  >Order of destruction
* [Move Constructors and Move Assignment Operators (C++)](https://docs.microsoft.com/en-us/cpp/cpp/move-constructors-and-move-assignment-operators-cpp?view=vs-2017)
* [Constructors (C++)](https://docs.microsoft.com/en-us/cpp/cpp/constructors-cpp?view=vs-2017)
  >Order of construction
* [C++: string 中find函数的用法以及string::npos的含义](https://blog.csdn.net/linwh8/article/details/50752733)
* [C++Boost序列化（Serialization）库教程](https://www.2cto.com/kf/201610/552182.html)
* [Eigen库数据结构内存对齐问题](https://blog.csdn.net/rs_huangzs/article/details/50574141)
* [ROS2入门教程-基本概念](https://www.ncnynl.com/archives/201801/2251.html)
* [ROS入门教程-1.1.10 创建ROS消息和ROS服务](https://www.ncnynl.com/archives/201608/508.html)
* [Smart Pointer Parameters](https://herbsutter.com/2013/06/05/gotw-91-solution-smart-pointer-parameters/)
* [Is it correct to return null shared_ptr?](https://stackoverflow.com/questions/37234969/is-it-correct-to-return-null-shared-ptr/37235251)
  >Yes, it is correct to initialize shared_ptr with nullptr. It is also correct to assign nullptr to shared_ptr
* [Explicitly deleting a shared_ptr](https://stackoverflow.com/questions/12321949/explicitly-deleting-a-shared-ptr)
* [C++ 如何让类对象只在堆或栈上创建](https://blog.csdn.net/qq_30835655/article/details/68938861)
* [成员变量在栈上还是堆上？](https://blog.csdn.net/djb100316878/article/details/52277531)
* [Classes And Memory Allocation](http://www.icce.rug.nl/documents/cplusplus/cplusplus09.html)
  >The move constructor: a constructor creating an object from an anonymous temporary object.  
  >匿名临时对象是函数的值返回结果,标准未定义放在栈还是堆，但一般放在栈
  >
  >A copy constructor is (almost) always available, even if it isn't declared in the class's interface.  
  >
  >Almost always as the declaration of a move constructor suppresses the default availability of the copy constructor. The default copy constructor is also suppressed if a move assignment operator is declared
  >
  >The copy constructor is simpler than the overloaded assignment operator in that it doesn't have to delete previously allocated memory.
* [Stack-Allocated Objects](https://people.eecs.ku.edu/~jrmiller/Courses/JavaToC++/StackAllocatedObjects.html)
  >java to c++
* [Strategies for the Allocation of Memory](http://www.modernescpp.com/index.php/strategies-for-the-allocation-of-memory)
  >Dynamic allocation  
  >Stack allocation  
  >Static allocation (placement new)  
  >Memory pool
* [Difference in make_shared and normal shared_ptr in C++](https://stackoverflow.com/questions/20895648/difference-in-make-shared-and-normal-shared-ptr-in-c)
  >share_ptr 管理两个实体，都在堆上
* [STL中vector的内存分配与正确释放](https://blog.csdn.net/bzhxuexi/article/details/40742161)
  >vector<type>(v).swap(v);  
  >string(s).swap(s);
* [What does std::vector look like in memory?](https://stackoverflow.com/questions/52330010/what-does-stdvector-look-like-in-memory)
  >The std::vector instance you have on the stack is a small object containing a pointer to a heap-allocated buffer, plus some extra variables to keep track of the size and and capacity of the vector.
* [RAII and smart pointers in C++](https://stackoverflow.com/questions/395123/raii-and-smart-pointers-in-c/395158#395158)
  >RAII This is a strange name for a simple but awesome concept. Better is the name Scope Bound Resource Management (SBRM). 
* [std::shared_ptr thread safety](https://stackoverflow.com/questions/14482830/stdshared-ptr-thread-safety/14485302#14485302)
  >It is only the control block itself which is thread-safe.
* [特征检测器 FeatureDetectorT](https://www.cnblogs.com/tianyalu/p/5468010.html)
* [shared_ptr to an array : should it be used?](https://stackoverflow.com/questions/13061979/shared-ptr-to-an-array-should-it-be-used)
* [SMART POINTERS AND DYNAMIC ARRAYS](https://zepix.wordpress.com/2015/09/21/smart-pointers-and-arrays/)
* [Opencv的KeyPoint和DMatch数据结构](https://www.cnblogs.com/TransTown/p/7396996.html)
* [[OpenCV]DMatch类和KeyPoints类：特征点匹配](http://www.mamicode.com/info-detail-2159374.html)
* [KeyPoint Matching 优化方式](https://blog.csdn.net/yangtrees/article/details/19928191)
* [vector 实现二维数组](https://blog.csdn.net/liushengxi_root/article/details/78945677)

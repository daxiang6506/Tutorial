# GDB

## ref

* [gdb调试的基本使用](https://blog.csdn.net/zdy0_2004/article/details/80102076)
* [如何在docker中进行gdb调试](https://www.jianshu.com/p/1c4476c3d0ee?from=groupmessage)

## command

```bash
start                                       run to main
clear                                       delete all breakpoints
watch/rwatch/awatch                         当写/读的时候断点，属于断点，可以用info break查看
c                                           继续运行程序直接运行到下一个断点
x/<n/f/u> <addr>                            以指定格式显示指定地址内容
return                                      强制返回当前函数(强制返回。return后面可以接一个表达式)
j N                                         跳转执行程序到第N行(如果后面没有断点则继续执行)
s                                           单步进入
n N                                         执行N次下一步
u                                           把光标停止在循环的头部，然后输入u这样就自动执行全部的循环
finish                                      执行完当前函数返回到调用它的函数
pwd                                         显示当前的所在目录
cd                                          相当于shell的cd命令
kill                                        终止一个正在调试的程序
info source                                 显示当前的调试源文件
info display/breakpoints

bt full                                     显示当前调用函数堆栈中的函数(也会显示出当前运行到了哪里(文件，行))
info frame N                                查看当前函数信(frame 命令切换后的栈帧)
f N                                         选择并显示栈帧N的内容  
up/down                                     移动栈帧
info args/locals                            显示选择栈帧的实参/局部变量
whatis i                                    看变量是哪个数据类型
where                                       查看当前位置
show dir                                    显示定义了的源文件搜索路径('$cdir' to refer to the compilation directory; '$cwd' to refer to the current working directory. '$cwd' is not the same as `.'---the former tracks the current working directory as it changes during your GDB session, while the latter is immediately expanded to the current directory at the time you add an entry to the source path.)
dir ../app                                  如果有多层目录，则在gdb中，用dir命令把你所想加入的文件的目录指定出来，然后b 命令就可以用了(如果你要指定多个路径，UNIX下你可以使用“:”，Windows下你可以使用“;”)

ptype                                       显示一个数据结构（如一个结构或C++类）的内容
```

```bash
gdb <program> core                          用gdb同时调试一个运行程序和core文件，core是程序非法执行后core dump后产生的文件。当程序非法崩溃的时候会产生一个core文件，然后使用这个命令，会直接定位到发生程序崩溃的位置。注意：有时需要设置系统命令“ulimit -c unlimited”才能产生core文件
```

```bash
print find_entry(1, 0)                      对程序中函数的调用
p *array@len                                动态数组
p 'f2.c'::x                                 查看文件f2.c中的全局变量x的值
print x=4                                   修改运行时候的变量值
print *a@10                                 会显示10个元素，无论a是double或者是int的都会正确地显示10个元素
print/p <expr>                              强制调用函数
print /x var                                用16进制显示(var)值
x  按十六进制格式显示变量。  
d  按十进制格式显示变量。  
u  按十六进制格式显示无符号整型。  
o  按八进制格式显示变量。  
t  按二进制格式显示变量。  
a  按十六进制格式显示变量。  
c  按字符格式显示变量。  
f  按浮点数格式显示变量
```

```bash
info display
disable display
enable display
delete display
display/disp
display/i $pc                               跟踪查看某个变量,每次停下来都显示它的值($pc是GDB的环境变量，表示着指令的地址，/i则表示输出格式为机器指令码，也就是汇编。于是当程序停下后，就会出现源代码和机器指令码相对应的情形)

```

```bash
watch i != 10                               检测表达式变化则停住(这里，i != 10这个表达式一旦变化，则停住,也是一种断点)
```

```bash
break                                       设置断点
info b                                      查询所有断点
b 10                                        设置断点，在源程序第10行  
b func                                      设置断点，在func函数入口处
   class::function或function(type,type)      指定函数名
   filename:linenum                         在源文件filename的linenum行处停住
   namespace::class::function               在名称空间为namespace的类class的function函数的入口处停住
break 46 if testsize==100                   如果testsize==100就在46行处断点
delete breakpoint                           删除所有断点
delete breakpoint N                         删除N号断点
disable breakpoint N                        禁止使用某个断点
enable breakpoint N                         允许使用某个断点
```

```bash
list <linenum>                              显示程序第linenum行的周围的源程序
list <function>                             显示函数名为function的函数的源程序
list                                        显示当前行后面的源程序
list-                                       显示当前行前面的源程序

```

```bash
x/<n/f/u> <addr>
n:  
>是一个正整数，表示显示内存的长度，也就是说从当前地址向后显示几个地址的内容。
f:  
>表示显示的格式，参见上面。如果地址所指的是字符串，那么格式可以是s，如果 地址是指令地址，那么格式可以是i。
u:  
>表示从当前地址往后请求的字节数，如果不指定的话，GDB默认是4个bytes。u参数可以用下面的字符来代替，b表示单字节，h表示双字节，w表示四字 节，g表示八字节。当我们指定了字节长度后，GDB会从指内存定的内存地址开始，读写指定字节，并把其当作一个值取出来。

x/3uh 0x54320                               表示，从内存地址0x54320读取内容，h表示以双字节为一个单位，3表示三个单位，u表示按十六进制显示
```
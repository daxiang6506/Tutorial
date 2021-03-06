# GIT

## reference

* [vim 复制/剪切/粘贴/撤销操作](https://blog.csdn.net/feng98ren/article/details/80509607)
* [vim 命令(全)](https://blog.csdn.net/zg_hover/article/details/1232018)
* [vim 空格和换行的删除和替换](https://www.cnblogs.com/clphp/p/5502026.html)
* [技巧：快速提高 Vi/Vim 使用效率的原则与途径](https://www.ibm.com/developerworks/cn/linux/l-cn-tip-vim/)
* [Linux vim如何实现文件中多行或者所有行相同列插入相同的字符串](https://blog.csdn.net/zz7zz7zz/article/details/45478273)
* [vi撤销命令（u和U），撤销上一次的操作](http://c.biancheng.net/view/558.html)
* [Vim 常用命令大全](https://www.jianshu.com/p/ebace108dd82)
* [超过 130 个你需要了解的 vim 命令](https://www.oschina.net/news/43167/130-essential-vim-commands)

## 宏

* 查看宏

  ```bash
  :reg a         查看宏a的内容
  ```

* 录制宏

  ```bash
  qa 'action' q  录制宏a
  ```

* 使用宏

  ```bash
  9@a            重复9次宏a  
  ```

## 命令

* 外部

  ```bash
  :r! ls  执行命令输出到当
  :r file 读文件到当前
  ```

* 特殊

  ```bash
  :set number         显示行号
  :set nonumber       关闭行号
  :set hlsearch       高亮匹配
  :set nohlsearch     关闭高亮匹配  
  :nohlsearch         关闭当前高亮匹配
  ggVG                全选
  .                   重复上次修改
  u/U                 回退上次操作/所有操作
  ;/,                 重复（回退）前一次输入的f/t命令
  n/N                 重复（回退）前一个搜寻动作/pattern
  &/u                 重复（回退）前一个替换动作 :s/word1/word2/
  ctrl + g            在文件中的位置
  ctrl + r            重做撤销操作
  ctrl + a            增加当前数字
  ctrl + x            减少当前数字
  J                   删除换行符,可以选中多行
  xp                  交换光标位置和之后位置字符
  ddp/ddkP            交换光标位置行和下一行/光标位置行和上一行
  ~                   将光标处字符大小写反转
  g~aw                将光标所在单词大小写反转
  guaw                将光标所在单词小写
  guu/UU              将光标所在行小写/大写
  >/>>                左移行，左移当前行
  +y                  复制到系统剪贴板
  +p                  粘贴到系统剪贴板
  "0p                 粘贴y命令的内容（d命令的内容不在0，0是y命令专用）
  [[: 跳转到上一个函数块开始，需要有单独一行的{。
  ]]: 跳转到下一个函数块开始，需要有单独一行的{。
  []: 跳转到上一个函数块结束，需要有单独一行的}。
  ][: 跳转到下一个函数块结束，需要有单独一行的}。
  [{: 跳转到当前块开始处；
  ]}: 跳转到当前块结束处；
  ci', di', yi'：修改、剪切或复制'之间的内容
  ca', da', ya'：修改、剪切或复制'之间的内容，包含'

  ```

* 跳转

  ```bash
  ``                  回到跳转之前位置，两个位置之间互跳
  ctrl + i            跳转到较新的位置，直到最新
  ctrl + o            跳转到较老都位置，直到最老
  ```

* 移动

  ```bash
  f        移动到光标右边指定字符上
  F        移动到光标左边指定字符上
  t        移动到光标右边指定字符前
  T        移动到光标左边指定字符前
  3f       移动到光标左边第3个指定字符上
  0/^      到行首/第一个非空白字符
  $        到行尾
  5$       5行后行尾
  gg       第一行
  G        最后一行
  10G      到第10行
  ( / ）   移动到句首/句尾
  { / }    移动到段首/段尾
  H        光标移动到这个屏幕的最上方那一行的第一个字符
  M        光标移动到这个屏幕的中央那一行的第一个字符
  L        光标移动到这个屏幕的最下方那一行的第一个字符
  Ctrl-d   屏幕向下移动半页
  Ctrl-u   屏幕向上移动半页
  Ctrl-e   向上滚屏
  Ctrl-y   向下滚屏
  zz/zb/zt 当前行置为屏幕正中央/底部/顶部
  +        次行行首
  10+      次10行行首
  -        前一行行首
  10-      前10行行首
  h/j/k/l  左/下/上/右
  10j      向下移动10行
  b/B      go to the [b]eginning of this word/String
  e/E      go to the [e]nd of this word/String
  w/W      go to the start of the following [w]ord/String
  ge/gE    [g]o back to the [e]nd of the previous word/String
  ```

* 删除/剪切

  ```bash
  d{motion}     删除{motion}移动方向的字符
  x             删除当前光标下字符
  2x            删除光标之后2个字符
  caw           删除光标所在单词，包括空白
  dd            删除1行
  5dd           删除5行
  d3l           向右删除3个字符
  d3k           向上删除3行
  D/d$          删除至行末
  d0            删除至行首
  D1G           删除至第一行
  DG            删除至最后一行
  dw            删除从当前位置到下一个单词词首
  diw           删除光标所在单词，不包括空白
  daw           删除光标所在单词，包括空白
  d4iw          删除4个单词
  4diw          删除4个单词
  nx            连续向后删除n个字符
  X             删除当前光标左边字符
  ```

* 修改

  ```bash
  c             删除命令，命令执行后会进入Insert模式
  s/cl          修改一个字符
  C/c$          修改到行尾的内容
  S/^c          修改一行
  r             替换字符,直接加回车，替换为换行符
  R             替换模式
  ```

* 插入

  ```bash
  o/A<CR>       当前行下插入1空行
  O/ko          当前行上插入1空行
  a             光标之后插入
  i             光标之前插入
  A/$a          行尾插入
  I/^i          行首插入
  3i            光标之后插入，输入完成ESC退出，输入重复3遍
  ```

* 选中

  ```bash
  V             line模式
  gv            重选上次高亮选区
  vt'char’      向右选择到字符'char'前
  </>           选中之后格式化，可以前面加数字
  u/U           选中变小写/大写
  V5G           选中当前行至指定行之间
  V5j           选中当前行以及上5行
  v5l           选中当前字符以及右边5个字符
  v$            选中到行尾
  v%            选中当前括号匹配内容
  viw           选中一个word，空白算一个word
  vaw           选中一个word，空白不算一个word
  vit           选中tag内容
  v4aw          选中4个word
  v3W           向后选中第3个字符串的第一个字符
  v3E           向后选中第3个字符串的最后一个字符
  v3B           向前选中第三个字符串的第一个字符
  Ctrl-v + s    选中矩形区域并按字符删除修改
  Ctrl-v + r    选中矩形区域并按字符修改
  Ctrl-v + C/S  选中矩形区域并按行删除修改 
  Ctrl-v + I    选中矩形区域并行首插入字符，可以用方向键移动 
  Ctrl-v + A    选中矩形区域并行尾插入字符，必须选中第一列 
  ```


* 粘贴

  ```bash
  P    光标之前粘贴
  p    光标之后粘贴
  ```

* 复制

  ```bash
  yy   复制游标所在的那一行
  yiw  复制一个word
  y4w  复制4个word
  nyy  复制光标所在的向下n行
  y1G  复制游标所在行到第一行的所有数据
  yG   复制游标所在行到最后一行的所有数据
  y0   复制光标所在的那个字符到该行行首的所有数据
  y$   复制光标所在的那个字符到该行行尾的所有数据
  ```

* 查找

  ```bash
  *       查找当前单词，要求每次出现前后为空白字符或标点符号
  g*      查找光标所在单词的字符序列，每次出现前后字符无要求
  /word   向光标之下寻找一个名称为 word 的字符串
  ?word   向光标之上寻找一个字符串名称为 word 的字符串
  fx      当前行查找字符x，;表示下一个
  Fx      反向当前行查找字符x，;表示下一个
  %       以匹配一个括号为目的移动
  50%     光标定位在文件的中间
  ```

* 替换（行模式下也可使用）

  >当前行寻找第一个word1这个字符串，并将该字符串取代为word2

  ```bash
  :s/word1/word2/
  ```

  >当前行寻找所有word1这个字符串，并将该字符串取代为word2

  ```bash
  :s/word1/word2/g
  ```

  >当前文件寻找所有word1这个字符串，并将该字符串取代为word2

  ```bash
  :%s/word1/word2/g  
  ```

  >在第n1与n2行之间寻找word1这个字符串，并将该字符串取代为word2

  ```bash
  :n1,n2s/word1/word2/g  
  ```

  >从第一行到最后一行寻找 word1 字符串，并将该字符串取代为word2

  ```bash
  :1,$s/word1/word2/g
  ```

  >选区，在Visual模式下选择区域后输入:，Vim即可自动补全为 :'<,'>

  ```bash
  :'<,'>s/word1/word2/g
  ```

  >当前行空格替换为回车

  ```bash
  :s/ +/\r/g
  ```

  
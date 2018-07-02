## 命令
* 特殊
  ```
  ggVG     全选
  ```
* 移动
  ```
  0/^      到行首/第一个非空白字符
  $        到行尾
  5$       5行后行尾
  gg       第一行
  G        最后一行
  nG       到第n行
  H        光标移动到这个屏幕的最上方那一行的第一个字符
  M        光标移动到这个屏幕的中央那一行的第一个字符
  L        光标移动到这个屏幕的最下方那一行的第一个字符
  Ctrl-d   屏幕向下移动半页
  Ctrl-u   屏幕向上移动半页
  Ctrl-e   向上滚屏
  Ctrl-y   向下滚屏
  zz/zb/zt 当前行置为屏幕正中央/底部/顶部
  +        次行行首
  n+       n次行行首
  -        前一行行首
  n-       前n行行首
  h/j/k/l  左/下/上/右
  10j      向下移动10行
  w        下一个单词第一个字符
  e        下一个单词最后一个字符
  b        前一个单词第一个字符
  ge       前一个单词最后一个字符
  ```
* 删除/剪切
  ```
  d        剪切选中
  x        删除当前光标下字符
  2x       删除光标之后2个字符
  c        改变命令，命令执行后会进入Insert模式
  caw      删除光标所在单词，包括空白 
  dd       删除1行
  5dd      删除5行
  d3l      向右删除3个字符
  d3k      向上删除3行
  D        删除至行末
  d0       删除至行首
  D1G      删除至第一行
  DG       删除至最后一行∂
  dw       删除从当前位置到下一个单词词首
  diw      删除光标所在单词，不包括空白
  daw      删除光标所在单词，包括空白
  nx       连续向后删除n个字符
  X        删除当前光标左边字符
  J        删除换行符
  ```
* 选中
  ```
  u/U           选中变小写/大写
  V5G           选中当前行至指定行之间
  V5j           选中当前行以及上5行
  v5l           选中当前字符以及右边5个字符
  v$            选中到行尾
  v%            选中当前括号匹配内容
  viw           选中一个word
  Ctrl-v + s    选中矩形区域并按字符删除修改
  Ctrl-v + r    选中矩形区域并按字符修改
  Ctrl-v + C/S  选中矩形区域并按行删除修改 
  Ctrl-v + I    选中矩形区域并行首插入字符，可以用方向键移动 
  Ctrl-v + A    选中矩形区域并行尾插入字符，必须选中第一列 
  ```
* 修改
  ```
  s    修改一个字符
  C    修改到行尾的内容
  S    修改一行
  r    替换字符,直接加回车，替换为换行符
  R    替换模式
  ```
* 插入
  ```
  o    当前行下插入1空行
  O    当前行上插入1空行
  a    光标之后插入
  i    光标之前插入
  A    行尾插入
  I    行首插入
  3i   光标之后插入，输入完成ESC退出，输入重复3遍
  ```
* 粘贴
  ```
  P    光标之前粘贴
  p    光标之后粘贴
  ```
* 复制
  ```
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
  ```
  /word   向光标之下寻找一个名称为 word 的字符串
  ?word   向光标之上寻找一个字符串名称为 word 的字符串
  n       重复前一个搜寻动作
  N       反向进行前一个搜寻动作
  fx      当前行查找字符x，;表示下一个
  Fx      反向当前行查找字符x，;表示下一个
  %       以匹配一个括号为目的移动
  50%     光标定位在文件的中间
  ```
* 替换
  ```
  :s/word1/word2/
  ```
  >当前行寻找第一个word1这个字符串，并将该字符串取代为word2
  ```
  :s/word1/word2/g
  ```
  >当前行寻找所有word1这个字符串，并将该字符串取代为word2
  ```
  :%s/word1/word2/g  
  ```
  >当前文件寻找所有word1这个字符串，并将该字符串取代为word2
  ```
  :n1,n2s/word1/word2/g  
  ```
  >在第n1与n2行之间寻找word1这个字符串，并将该字符串取代为word2
  ```
  :1,$s/word1/word2/g
  ```
  >从第一行到最后一行寻找 word1 字符串，并将该字符串取代为word2
  ```
  :s/ +/\r/g
  ```
  >当前行空格替换为回车
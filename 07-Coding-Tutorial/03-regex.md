# 正则表达式

## 资源

* [利用python re提取文件中的块内容（多行）](https://blog.csdn.net/liu35937266/article/details/78354622)
  >用.*?做懒惰匹配（否则所有的会被匹配成一条，达不到分隔的效果）

* [正则匹配以xx开头以xx结尾的单词](https://blog.csdn.net/qq_32623363/article/details/78808132)
  >对于字符串abcgabc  
  >贪婪模式– a.*c –得到的答案为：abcgabc  
  >懒惰模式– a.*?c –得到的答案为：abc,abc  
  >贪婪模式下会尽量匹配最长的字符串，而懒惰模式会尽量匹配最短的字符串  

* [正则表达式 - 语法](http://www.runoob.com/regexp/regexp-syntax.html)
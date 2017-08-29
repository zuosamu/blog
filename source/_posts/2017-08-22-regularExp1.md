---
title: '正则,新手教学,立即上手(元字符)'
date: 2017-08-22 14:13:59
categories: regular正则教学
tages:
tags:
---
## 正则,又叫正则表达式(英语:Regular Expression,简称:regEx)
是计算机科学的一个概念。正则表达式使用单个字符串来描述、匹配一系列匹配某个句法规则的字符串。在很多文本编辑器里，正则表达式通常被用来检索、替换那些匹配某个模式的文本[来之wiki](https://zh.wikipedia.org/wiki/%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F)
## 正则的发展简介
最初的正则表达式出现于[理论计算机科学](https://zh.wikipedia.org/wiki/%E7%90%86%E8%AB%96%E8%A8%88%E7%AE%97%E6%A9%9F%E7%A7%91%E5%AD%B8)的[自动控制理论](https://zh.wikipedia.org/wiki/%E8%87%AA%E5%8A%A8%E6%8E%A7%E5%88%B6)和[形式化语言](https://zh.wikipedia.org/wiki/%E8%87%AA%E5%8A%A8%E6%8E%A7%E5%88%B6)理论中。在这些领域中有对计算（自动控制）的模型和对形式化语言描述与分类的研究。
1940年，[沃伦·麦卡洛克](https://zh.wikipedia.org/wiki/%E6%B2%83%E4%BC%A6%C2%B7%E9%BA%A6%E5%8D%A1%E6%B4%9B%E5%85%8B)与Walter Pitts将[神经系统](https://zh.wikipedia.org/wiki/%E7%A5%9E%E7%BB%8F%E7%B3%BB%E7%BB%9F)中的神经元描述成小而简单的自动控制元。
1950年代，数学家[斯蒂芬·科尔·克莱尼](https://zh.wikipedia.org/wiki/%E6%96%AF%E8%92%82%E8%8A%AC%C2%B7%E7%A7%91%E5%B0%94%C2%B7%E5%85%8B%E8%8E%B1%E5%B0%BC)利用称之为“正则集合”的数学符号来描述此模型。[肯·汤普逊](https://zh.wikipedia.org/wiki/%E8%82%AF%C2%B7%E6%B1%A4%E6%99%AE%E9%80%8A)将此符号系统引入编辑器QED，随后是[Unix](https://zh.wikipedia.org/wiki/UNIX)上的编辑器ed，并最终引入[grep](https://zh.wikipedia.org/wiki/Grep)。自此以后，正则表达式被广泛地应用于各种 Unix或[类Unix](https://zh.wikipedia.org/wiki/%E7%B1%BBUnix%E7%B3%BB%E7%BB%9F)系统的工具中。
## 正则的使用
### 元字符介绍
"^" ：^会匹配行或者字符串的起始位置
"$"  ：$会匹配行或字符串的结尾
"\b" :不会消耗任何字符只匹配一个位置，常用于匹配单词边界
"\d": 匹配数字
"\w"：匹配字母，数字，下划线
"\s"：匹配空格
"."：匹配除了换行符以外的任何字符这个算是"\w"的加强版了"\w"不能匹配空格 
"[abc]": 字符组  匹配包含括号内元素的字符,这个比较简单了只匹配括号内存在的字符
我的理解：元字符中除了"^","$","\b"之外,其他的元字符都是实体。
啥叫实体：就是在正则匹配中,对应着一个字符位。
#### 例子1
我们现在要匹配一个电话号码，假设这个电话号码是:1234-1234567
现在我们要去校验我们输入的电话号码是这个指定的号码怎么做呢？
我们可以直接校验：/1234-1234567/(正则可以使用//表示调用)
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-1.png %}
上图我们可以看见只有1234-1234567这个字符串通过了我们的正则表达式
#### 例子2
当然我们一般不会像上面一样使用正则，不然那就显得太蠢啦！
我们继续接着上面的例子继续：
现在我们要匹配一个国内的座机号码怎么弄呢？
我们都知道国内的电话号码的格式是:XXXX-XXXXXXX(由数字组成)
"\d"匹配对位的数字字符
我们可以校验：/\d\d\d\d-\d\d\d\d\d\d\d/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-2.png %}
我们可以看见满足格式的，全是数字的前3个字符串满足要求，而带有字母的后两个不满足要求
#### 例子3
现在我们要把这个正则改一改，以便符合我们的需求，我们现在要把前面的区号(XXXX)扩展一下，以便我们统治世界以后，地区号码不够用，我们现在允许区号可以使用字母，数字，或者下划线。
"\w"：匹配字母，数字，下划线
我们可以校验：/\w\w\w\w-\d\d\d\d\d\d\d/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-3.jpg %}
#### 例子4
现在我们再把这个正则改一改，现在我要求区号的第一个字符是[a-d]其中的一个，要怎么做呢？
"[abc]": 字符组  匹配包含括号内元素的字符
我们可以校验：/[abcd]\w\w\w-\d\d\d\d\d\d\d/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-4.png %}
当然我们可以这么写：/[a-d]\w\w\w-\d\d\d\d\d\d\d/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-5.png %}
可以发现跟上面是一样的
到这里我们还有"\s","."没有讲解了，但是这个跟上面的是一样的，所以就不讲解了
#### 例子5
我们想在回到正则：/\d\d\d\d-\d\d\d\d\d\d\d/
现在我们要去校验这样一个字符串：121234-1234567-1234567会发生什么有趣的事呢？
大致如下：
{% img http://ov2t5xkda.bkt.clouddn.com/image/qiniuyun/regex-rule.png %}
那现在我们只想要匹配第二个呢？
我们可以使用：
"$"  ：$会匹配行或字符串的结尾
我们的正则：/\d\d\d\d-\d\d\d\d\d\d\d$/
换句话说,"$"只会比对,字符串结尾满不满足条件
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-6.png %}
#### 例子6
能匹配结尾，那开头呢？当然也能匹配啦！
"^" ：^会匹配行或者字符串的起始位置
我们来看这个例子：
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/rexge-1-7.png %}
#### 例子7
来一个实际中可能会遇到的问题：
我们要匹配一个正则，只能通过0～9的一位数，那我们按照我们上面学习，我们怎么写呢？
我们可以：/\d/也可以/[0-9]/还可以/[0123456789]/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-8.png %}
欸？？？
怎么不对呢？
因为正则是按照占位符，移一位比对的，如果比对成功，既比对成功,55含有两个"5"+"5",所以他是能通过正则的,那不满足我的需求咋办？
我们可以想到例子5和例子6
"^"和"$",我们让开头的匹配成功=结尾的匹配成功，是不是就保证它的唯一性了呢
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-1-9.png %}
## 结语
到这里我们已经掌握了最基本的正则使用方法了，希望对大家有帮助。(博客还在建设之中，有些功能还没有实现，敬请期待)
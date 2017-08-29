---
title: 正则,新手教学,立即上手(量词)
date: 2017-08-29 10:17:56
categories: regular正则教学
tages:
tags:
---
## 起词
量词其实不是必须的,为啥呢?我们记得"\d\d\d\d-\d\d\d\d\d\d\d"是满足要求的,只是不太美观,BUT,我们都是追求艺术的疯子。所以我们怎么把代码写得跟优雅呢？今天就给大家说说量词。
## 量词
### 特征
量词可以类是的理解成我们一般语言学里面的形容词。
它不是主体,也就是说它不占坑[],并不是占位符
它只描述(形容)它前面的一个单元(坑)(占位符)
"*"：(全部) 重复零次或更多[0,+∞)
"+": (有)   重复一次或更多次[1,+∞)
"?": (占有) 重复零次或一次[0,1]
"{n}": (必有) 重复n次
"{n,m}"：(大概有)  重复n到m次[n,m]
"{n,}":(至少有)  重复n次或更多次[n,+∞)
#### 补充
量词这里有6个常用的，我们来看看,'*','+','?'都是单字符的，功能也很单一，而'{n}','{n,m}','{n,}'是复合型的，可以理解成是前3个的加强版
#### 例子1
当我们匹配: /a*/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-1.png %}
当我们匹配: /ab*/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-2.png %}
当我们匹配: /aab*/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-3.png %}
我们可以看出,他只匹配出了紧接着'b'的全部的'a'or'aa'
#### 例子2
当我们匹配: /aab+/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-4.png %}
#### 例子3
当我们匹配：/aab{2}/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-5.png %}
#### 例子4
当我们匹配：/aab{0,3}/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-6.png %}
#### 例子5
当我们匹配：/aab{1,}/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-7.png %}
## 温故知新
我们在第一节说过一个正则:/\d\d\d\d-\d\d\d\d\d\d\d/,我们现在来改造一下这个正则使它变得更漂亮：
/\d{4}-\d{7}/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-8.png %}
现在我们给它加上绝对性:
/^\d{4}-\d{7}$/
{% img http://ov2t5xkda.bkt.clouddn.com/image/regex/regex-3-9.png %}
## 结语
到这里，其实我们已经能够写出很多常用的正则了，而且能够美化它，下节我们将进入深水区,慢慢揭开正则的面纱
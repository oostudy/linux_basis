# 正则表达式

## 正则表达式的发展史
* 20世纪40年代:提出正则表达式的最初想法的人是两个"神经学家"，
  他们认为大脑的神经系统的神经元层面就是这样工作的，
  所以正则表达式可以被看作是一种模拟大脑模型。
* 20世纪50~60年代: 理论数学界给这个模型起了一个名字，叫做“**正则集合**”。然后斯蒂芬·科尔·克莱尼（一个数学家）
  发明了一套表示这个正则集合的方法，就是我们今天看到的“**正则表达式**”。
* 1968年: Unix发明人Ken Thompson首次成功运用正则表达式，开发出支持正则的编辑器qed。
  这是首次将正则表达式在计算机上大放光彩，从数学理论的证明转向了实际运用。此后，
  正则表达式在计算机领域开始不断壮大。
* 1986年: 在正则表达式出现后的一段时间里，诸子百家争鸣，乱世显现。这一年诞生了第一个较为统一的标准
  —— ``POSIX``，POSIX将正则表达式分为了两种标准``Basic Regular Expressions(BREs)``和
  ``Extended Regular Expressions(EREs)``
* 1987年12月: ``Perl``的出现，几乎对正则表达式的争论画上了句号。从此，业界最强的正则引擎诞生。
  ``PCRE``正则引擎的出现，几乎广泛应用于之后所有出现的编程语言上。

## 正则表达式的应用场景

*模式(pattern)* 的匹配，如文本/字符串等内容的匹配与解析/修改，验证密码复杂性等。

**不适合用作逻辑判断**，如以下这个用于判断日期合法性的正则就属于一种糟糕的实践:

```
(([0-9]{2}([02468][048])|([13579][26])))(02)(([0][1-9])|([1-2][0-
9]))|(([0-9]{2}([02468][123579])|([13579][01345789])))(02)(([0][1-
9])|([1][0-9])|([2][0-8]))|([0-9]{4})(([0](1|3|5|7|8))|10|12)(([0][1-
9])|([1-2][0-9])|30|31)|([0-9]{4})(04|06|09|11)(([0][1-9])|([1-2][0-
9])|30)
```

这样的写法如果是用在教学中，确实是一个不可多得的好例子，但要用在
实际开发中，就不太合适了。

首先，任何人看了这样长的一个正则表达式，心 里想的第一个问题就是该如何看懂它--太复杂！

其次，在编写它的时候，逻辑思路必须特别特别清晰，因为稍微一个不留神，就可能遗漏某个环节--难编写！

第三，正则表达式在使用之前都是需要编译的，语法越复杂编译起来也就越慢，
而且执行起来也不见得会比我们普通编写的程序代码跑得快--效率低！

所以，一定要记住，正则表达式的优势是进行样式匹配，而不是具体的逻
辑处理。只有正确地认识到这一点，在程序编写时合理地使用正则表达式，才
能明确问题的关键所在，得出一个最佳的解决方案。

## 如何学好正则表达式?
* 正则表达式没有你想的那么复杂，不要上手就先觉得难
* 使用正则表达式之前，先分析场景是否适合使用正则
* 使用正则前，一定要确认 **正则引擎**(幸运的是，由于有标准的出现，绝大多数正则引擎的元字符和意义都相同)
* 多在实际运用中体会，常用的元字符需要记住
* 写正则前，不是先想正则怎么写，而是先找规律——要匹配的文本/字符串有什么规律，满足什么样的模式？
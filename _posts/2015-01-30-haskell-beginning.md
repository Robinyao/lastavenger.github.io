---
layout: post
title: Hello Haskell
tags: Haskell
---
我想学Haskell的原因在很大程度上拜轮子叔所赐，前一阵子在图书馆意外发现了一本「Haskell趣学指南」，这下子更没有不学的理由了。<br>

多说一句，有趣的是这本书的译者之一竟然是 Fleurer，我曾经好几次发邮件询问他有关OS的事情，没想到在图书馆借到了他的书。。。另一个译者是蓝莲花的宋方睿大神，, 曾经在中大听过蓝莲花的宣讲会， 可惜当时他并没有在场。<br>
不得不说世界真是太小了.<br>

好了说点正事。
##安装
Haskell的编译器是GHC，我的系统是openSUSE，安装ghc可以直接`sudo zypper in ghc`, 但是比ghc更方便的是Haskell Platform, 安装同样可以`sudo zypper in haskell-platform `, 在 Windows 上则可以直接去官网下载安装包。

##随便说说
因为借书的时候已经是考试周的前夕，所以到现在翻看书的时间仅限于之前在阅览室里无聊的那一会还有回家的路上，现在是第五章，似乎有点初窥门径的感觉，又怕是自己想得太简单了。<br>
总得来说是这么些感受吧：<br>

* 列表推导式很神奇，`[x | x <- xs , x < 100]`,其形式类似于之前用来描述集合的公式，之前上离散的时候不明白为什么要有谓词这个鸡肋的概念，原来可以用在这里;
* 类型类（Type Class）: 有点像是接口之类的东西，这个类型类的实例具有特定的特征， 类型类也必须为这些实例提供对应的方法，两个数如果可比较（Ord），那么就能判断这两个数的相等性（Eq）; 
* 模式匹配（Pattern Macthing）: 一开始我自动脑补成了函数的重载，但其实不是重载，因为函数的参数根本就没有改变。 是不是觉得模式匹配只是可以避免`if-else`而已，类似于case？ 后来书里也说到了模式匹配就是case的语法糖，我暂时是说不出模式匹配到底有什么特别的地方，但是在写递归函数的时候模式匹配用起来特别顺手；
* 递归： 拜模式匹配所赐，递归在Haskell写起来真是漂亮极了。
* 柯里函数 （Curry Function）： 请注意他的命名来自于 Haskell Curry, 对，和Haskell这个名字的来源一样。柯里函数的出现解释了为什么接受多个参数的函数的声明必须类似于`a -> b -> c` 而不是 `a, b -> c`, 柯里函数是一个一元函数， 每次调用只接受一个参数， 并返回一个固化了该参数的一元函数，书里的比喻非常有趣，对于代码：

```haskell
multThree :: Int -> Int -> Int -> Int
multThree x y z = x * y * z
```

> 你可以将函数看做小工厂， 它们会取一些原材料，然后生产一些东西，对于上面的代码，执行 multThree 3 5 9，<br>
> 我们将数值3喂给multThree工厂，这个工厂产生了一个更小的工厂，这家小工厂得到数值5，继续搞出来一家小工厂，<br>
> 第三家工厂得到数值9,产出最终的结果，也就是135。<br>

```haskell
qsort :: (Ord a) => [a] -> [a]
qsort [] = []
qsort (x:xs) = qsort lteq ++ [x] ++ qsort gt
    where lteq = [a | a <- xs, a <= x]
          gt = [a | a <- xs, a > x]
```

对于我这种初学者来说，最有诱惑力也最后成就感的自然就是三行快排了。。。诶，去掉声明就是三行了。<br>
当然还会有更加厉害的实现，不过，先这样好了。
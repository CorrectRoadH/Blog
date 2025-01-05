---
title: "我在过去一年中最常犯的编程错误"
description: 编程的错误
published:  2025-01-02
tags: [编程]
category: 技术
draft: true
---

## 数量级，因为数量级导致的性能上的问题
写功能的时候常常忽略这个点，从而影响性能问题让软件看起来像出Bug一样，最开始是关注算法复杂度，想着只要O(N)就好了。然后总爱忘记那些极端情况。就算是O(N)，也常常到了测试阶段才发现当数量到了成百上千就会有问题。
这时就算加上并发也无济于事，只能再回头改产品设计，再加上一个loading的交互。

## 想当然
在这里犯过的错误太多了。总是想当然的认为代码能跑，在出问题之前怎么也想不到会有这里会有问题。然后Bug一出来，只能一拍脑门，我当初太想当然了。
最近的一个例子在做虚拟机的时候，把UEFI支持升级到安全UEFI。测试了几个系统都正常。结果上线之后才发现Debian系统可不认这一套。启动失败。

## 不敬畏老代码，尽管可能不老，也是你自己写的

对于上面的解决方案就是敬畏老代码。在过去能跑的代码中，你永远也想不到会有什么坑点，所以应该去敬畏它，而不是觉得这里没有问题去改变它。比如我可以新开一个UEFI，装好的系统依然使用旧的， 新安装的系统使用新的UEFI。大家接手前辈的屎山时，肯定都会这样想，但是只有屎山会这样吗
但是上文提到的虚拟机中的启动引导的问题，虚拟机相关的代码就是我前段时间刚写的，所以我没有产生什么想法。做了一个愚蠢的设计
## 太敬畏老代码，没有让代码跟着产品一起走

但是在另一个项目中，我总感觉不舒服，那是一个相对有点月岁的项目，在跟着产品改变产品需求，很多功能在原来的函数上面加代码。或者直接加抽象层做额外的功能。 到了今年再回去看这个项目的代码，越看越难受。因为代码调用的层次变的非常的复杂。有些函数内部的实现与函数名无关(但是interface已经定了，改不同的imp的函数要改太多)。

还有许多术语的函数已经发生变化，在刚写代码时，用的某一个词在现在的含义已经发现了变化。

## 过度设计
上面那个项目就是明显的过度设计，在产品抽象之初就做了很多interface，套了几层抽象。想着在未来产品的变化，我怎么都能应付。结果到了后面，根本抽象不到产品的设计。之前的过度设计反而变成了牢笼。

## 没有设计
现在越来越觉得代码是个艺术，取舍与平衡




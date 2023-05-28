---
title:  "《crafting interpreters》学习总结"
date:   2023-05-27 13:21:00 +0800
categories: learning
tags: learning, compiler
---

花了三个月的时间学完了《crafting interpreters》，对程序的编译运行有了更深的认识，做一下总结，以便回顾。这本书设计了一个名为lox的脚本语言，用Java和Ｃ分别实现了jlox和clox两种解释器。jlox依赖Java的对象内存管理，用少量的代码完成了代码的词法和语法的解析，以及AST的解释运行。clox则更加底层，通过解析生成字节码，并实现了虚拟机来执行字节码，手动完成了栈和堆的内存管理。

书中没有太多大段的编译理论，而是一步一步带领读者实现了源码的解析执行，在需要的时候才会对相关概念作讲解。从一个最小的解释器开始，一点点的增加功能，循序渐进，很适合学习实践。跟随书中内容，我用C++实现了lox的解释器，jlox的部分更多的使用C++的继承、多态、泛型模板和智能指针等面向对象的内容，而clox的部分则更多的使用了C的方法。仓库的地址在[crafting-interpreters](https://github.com/ArisQ/crafting-interpreters)。

闲话少说，下面会对学习过程中比较印象深刻的点作一些总结。

## 编译概览

![compiler]({{site.images}}/{{post_name}}/compiler.png)

根据书中的图
一门编程语言从源码文本，到最后解释或编译成二进制执行，是一个抽象程度不断提高的过程
lexer  parser interpreter & vm

## stack
## gc

## closure
闭包的捕获upvalue

## nan boxing
优化


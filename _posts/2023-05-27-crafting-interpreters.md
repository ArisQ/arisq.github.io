---
title:  "《crafting interpreters》学习总结"
date:   2023-05-27 13:21:00 +0800
categories: learning
tags: learning, compiler
---

工作之余花了三个月的时间学完了[《crafting interpreters》](http://www.craftinginterpreters.com/)，对程序的编译运行有了更深的认识，做一下总结，以便回顾。这本书设计了一个名为lox的脚本语言，用Java和Ｃ分别实现了jlox和clox两种解释器。jlox依赖Java的对象内存管理，用少量的代码完成了代码的词法和语法的解析，以及AST的解释运行。clox则更加底层，通过解析生成字节码，并实现了虚拟机来执行字节码，手动完成了栈和堆的内存管理。

书中没有太多大段的编译理论，而是一步一步带领读者实现了源码的解析执行，在需要的时候才会对相关概念作讲解。从一个最小的解释器开始，一点点的增加功能，循序渐进，很适合学习实践。跟随书中内容，我用C++实现了lox的解释器，jlox的部分更多的使用C++的继承、多态、泛型模板和智能指针等面向对象的内容，而clox的部分则更多的使用了C的方法。仓库的地址在[crafting-interpreters](https://github.com/ArisQ/crafting-interpreters)。

闲话少说，下面总结一下学习过程中印象比较深刻的点。

## 编译概览

<!-- ![compiler]({{site.images}}/{{post_name}}/compiler.png) -->
![compiler](../images/crafting-interpreters/mountain.png)

编译过程从源码由解析成token，再到AST是一个抽象程度不断提高的过程。源码是文本的字符流，由词法器解析生成token流，token是语法的基本元素，再由语法解析器生成AST。字符流之于token类似于token之于AST。从AST生成可执行文件，则是从抽象到具象的过程。

![string](../images/crafting-interpreters/string.png)
![tokens](../images/crafting-interpreters/tokens.png)
![ast](../images/crafting-interpreters/ast.png)

整个过程很像是从字符串反序列化成struct，再从struct序列化成字符串，只不过输入的是对人来说可读性更好的表示，而输出的是对机器友好的表示形式，AST则是程序的建模模型。类似的源码的格式化工具Formatter可以将解析到的AST再序列化成对人友好的表示形式。

```
ast = humanParser.Unmarshal(source)
binary = machineParser.Marshal(ast)
```

compiler和vm相互配合

根据书中的图
一门编程语言从源码文本，到最后解释或编译成二进制执行，是一个抽象程度不断提高的过程
lexer  parser interpreter & vm

## stack
FILO
栈平衡


## gc

## closure
闭包的捕获upvalue

## nan boxing
优化


* 图片来源[craftinginterpreters](https://github.com/munificent/craftinginterpreters)
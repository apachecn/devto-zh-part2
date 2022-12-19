# 使用 JavaScript 的开发人员的设计模式-第二部分

> 原文：<https://dev.to/olivermensahdev/design-patterns-for-developers-using-javascript---part-two--3p39>

# 创意设计模式

在[之前的文章](https://dev.to/omensah/design-patterns-for-developers-using-javascript----part-one--b3e)中，我们看了一下设计模式，它的定义，历史，以及与软件工程的结合。本文主要关注创造性设计模式，这是软件工程中的一种设计模式。创造性设计模式用于创建新对象。当创建某种类型的新对象时，有几种设计模式需要考虑。让我们从构造器模式开始。

## 构造器模式

构造函数模式并不是来自于四人帮。但是当我们用 JavaScript 构造新的对象时，了解更多关于这种模式的知识是非常重要的。构造器模式用于创建具有自己的对象范围的新对象。JavaScript 的对象系统是基于原型的，所以在构造函数模式中,“new”关键字用于从函数中创建对象。这是通过在函数前面放置关键字“new”来实现的。因此，每当这个关键字被放在一个函数前面，它就创建一个构造函数。当这个构造函数被执行时，会发生四件事。1)一个全新的物体被创造出来。2)它将该对象链接到一个对象原型。
3)它将“this”关键字绑定到新的对象范围。
4)然后返回‘this’。

ES6 将“class”关键字用于`desugar`对象的创建，但它最终传递给了原型。
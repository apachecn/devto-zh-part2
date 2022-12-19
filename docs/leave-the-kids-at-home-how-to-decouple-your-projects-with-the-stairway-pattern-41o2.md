# 把孩子留在家里:如何用楼梯模式分离你的项目

> 原文：<https://dev.to/makingloops/leave-the-kids-at-home-how-to-decouple-your-projects-with-the-stairway-pattern-41o2>

当你创建一个新类的时候，你知道应该把它放在你的解决方案的什么地方吗？或者你只是把它放在类似的东西旁边，然后称它为好的？

想想你写的最后一个类——你认为它在正确的位置吗？是不是*灵活*和*易变*？

除了作为开发人员的行话(除了在我的[如何组织你的项目](https://purple.pizza/how-to-organize-your-projects/)文章中列出的漂亮策略)，你知道那实际上*看起来*会是什么样子吗？

除非有人向你解释，否则你最终可以凭直觉以某种方式编写代码*简单地说*，因为它与周围的代码匹配，但没有任何*真正的*专业考虑。

幸运的是，当我继续阅读 Gary McLean Hall 的《C# 自适应代码》这本书时，我带来了更多专业开发人员的好消息。

本文介绍了一种在类设计中被称为楼梯模式的技术。这种模式将保持您的代码松散耦合，并且作为副作用，将改进项目组织。

这是一种让你感觉像一个负责任的成年人的技巧，就像学习如何换一个漏气的轮胎。

## 随从反模式

在对模式进行介绍之前，作者首先解释了我们应该避免的反模式，即 Entourage 反模式。

简而言之，Entourage 反模式是**将你的实现和它们的接口放在同一个项目中。**

现在，当我读到这篇文章时，我很高兴，因为我从一开始就一直这么做，所以我知道我将要学到一些东西。

作者提到了这可能是个坏主意的几个原因:

首先，通过将实现放在那里，一个不太有经验的开发人员可能会尝试将`new`和*硬编码*到客户端类中，尽管接口已经存在。看一看[我之前的依赖注入文章](https://purple.pizza/why-should-you-use-dependency-injection/)，了解为什么硬编码依赖是一种代码味道。

第二，之所以称之为 Entourage 反模式，是因为客户端可能需要引入他们不需要的程序集。

在写这篇文章的时候，我正在开发的一个应用程序中有一个很好的例子。这个应用程序提供了一个利用 DocuSign 的电子签名功能，DocuSign 是一个非常受欢迎的电子签名平台，它有自己的 API 来管理整个文档签名流程。

当我们构建这个特性时，我们编写了一个`IESignatureService`接口，这样我们以后就可以用更便宜的东西或自己开发的东西替换 DocuSign。现在，尽管我们正在使用一个接口，但是在同一个项目中，`DocuSignService`实现(依赖于`DocuSignAPIClient`库集合)*位于它旁边。这个项目碰巧也是一个非常大的项目，包含许多与电子签名无关的其他业务逻辑。*

当您查看使用该业务逻辑项目的每个项目的`bin`目录时，问题就显现出来了。`DocuSignAPIClient.dll`存在于所有的*中！*。

该 DLL 是业务逻辑项目的随行成员，即使在不需要的时候也跟着它。

## 楼梯图案

为了解决这个问题，我们应用了楼梯模式，这只是将实现放在一个单独的程序集中。

客户端应该只依赖于一个接口，该接口可以与客户端位于同一个项目中，也可以位于单独的程序集中。它被称为楼梯模式，因为显示依赖关系的 UML 图看起来…像楼梯。

[![UML Diagram showing the stair shape of dependencies](../Images/fe1be7936a4570022c6a11538de5b40c.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--DEdikfhn--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://purple.pizza/public/stairway.jpg)

对于我们的电子签名示例，我们可以将我们的`DocuSignService`放在一个单独的`ServiceImplementations`项目中，这样它就可以从业务逻辑项目中分离出来，直到需要它的时候。

但是乔，你最终还是要打电话给`new`，所以随行人员总会在某个时候出现，对吗？

是啊！如果您使用依赖注入，您的实现将在应用程序的入口点被实例化，类似于 IoC 容器。但好处是，*即*是*只有*的地方`new`才会被调用。使您能够非常容易地交换实现。

我在阅读时更多地思考了这个问题，发现了这本书作者本人的非常有用的 StackOverflow 回应。阅读它是强制性的！

## 何时使用

我认为这种模式对于大多数服务类来说很方便。

不过，有一件事我不确定，那就是重构还没有用依赖注入构建的成熟代码库。与现有模式保持一致会更好吗？

关于一致性的补充说明:我喜欢这个比喻*五本书堆在一起，一本放在书架上比所有六本书堆在一起更好*，这是我在[看到的一篇名为《宜居代码](https://dev.to/jhotterbeekx/livable-code-embrace-the-practical-mess--46d6)的优秀文章，作者是 John Hotterbeekx。在所有这些*质朴、适应性强、干净的代码*演讲之后，这篇文章将帮助你在现实中立足。

作者还提到了一个普遍的担忧:实现这种模式可能会导致您的解决方案中项目数量的大幅增加，但他没有解释为什么不会出现这种情况。你会注意到在 StackOverflow 的问题中，其他人也有同样的担心。

你怎么想呢?你会简单地把所有的服务实现都放到一个项目中吗？

我想这取决于你的应用程序做多少不同的事情。对于我所开发的“除了厨房水槽以外的一切”的业务线应用程序，考虑到要重构的特性数量，实现这样的模式似乎令人生畏。

另一方面，我可以开始把隐喻的书放在书架上，并与我的团队沟通，这将是向前发展的新实践。

如果从事一些非常新的工作，我会毫无疑问地把这作为一个标准做法。
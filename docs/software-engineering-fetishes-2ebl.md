# 软件工程癖

> 原文：<https://dev.to/quii/software-engineering-fetishes-2ebl>

软件工程中有一些概念/原则被过分强调和优先考虑，而没有足够的*实际思考*。

*   到达第一个字节的时间
*   干燥的
*   这是一个非常值得一读的提交历史

团队将引入复杂的软件开发过程，停止所有的对话和思考，带来怪异和奇妙的技术选择来适应这些事情。

它们确实有一些价值，但是人们喜欢沉迷于它们而从不考虑成本。

## 时间到第一个字节

这是非常重要的，我们希望我们的网站在用户第一次访问他们的时候能够快速响应。

### 会发生什么

*   用上个月发布的框架构建一个 SPA，这样我们就可以继续向用户铲去 12mb 的无用资源。
*   网站表现仍然很糟糕，但至少*一些东西*很快出现了！
*   没完没了的重写，用构建/打包工具乱搞
*   网站没有 Javascript 就无法运行。

### 你应该做什么

你的网站*的性能比一个指标*更复杂，过分强调第一个字节的时间可能会损害其他一切。

思考一下:

*   请求总数
*   资源规模
*   执行 JS 对 CPU 的影响
*   它是多么的可缓存

## 干

DRY(不要重复自己)是指你将一些重复的代码重构为一个函数/类/接口/任何东西，以便它可以在其他地方重用。

重复代码很烦人，而且很浪费。如果你想修复一个 bug，而你有重复的代码，那就太可悲了。

### 会发生什么

*   怪异的弗兰肯斯坦函数/类，带有可选参数或布尔标志，传递给松散相关的概念，*但不是真正的*。
*   **强耦合**

### 你应该做什么

*   如果一个*概念*被两个以上的事物共享，你可以安全地重构。*只要拖住*。有人聪明地说，糟糕的抽象比没有抽象更糟糕。等到很明显*真的有事情*在那里干起来。
*   如果你最终给函数添加了标志，使它们的行为不同，这就是一个危险信号。
*   当做一个简单的改变时，会有很多测试失败吗？很多编译问题？这通常是紧耦合的标志，这通常是由于工程师过于担心编写枯燥的代码。
*   承认制作可重用的代码是困难和危险的。对于可重用服务，将其乘以 10。

## 一部真正令人惊叹的读犯史

我们希望人们可以通过查看 git 历史来了解项目变更背后的动机。

我们通常不会直接接受 master 中的更改，而是坚持在合并之前对精心制作的 pull 请求进行评估。

### 会发生什么

*   实际上，发布软件变成了一场疯狂的讨论，充满了自行车脱落。对于昨天就应该发布的最琐碎的更改，拉请求会持续几天、几周。
*   招聘广告仍然兴高采烈地说他们实践持续集成，同时开发人员有大量的时间来处理合并冲突，或者因为竞争的拉请求而害怕改变代码。
*   仍然没有人有任何真正的希望仅仅通过查看 git 历史来理解代码库，因为你当然不能。你通过阅读和改变来理解一个代码库。

### 你应该做什么

*   好的描述性测试。
*   结对编程。
*   试用[ADR](https://github.com/npryce/adr-tools)。
*   互相交流，建立团队。

对此有一些警告。对于分布式团队来说，拉取请求是有意义的，因为它们有助于对话等。您承认这种方法的限制意味着您将比其他团队迭代得更慢。

如果你在一个协同工作的团队中，想要快速构建和迭代一个产品，这种方法是非常浪费的。就以最快的速度推给师父，互相通话。
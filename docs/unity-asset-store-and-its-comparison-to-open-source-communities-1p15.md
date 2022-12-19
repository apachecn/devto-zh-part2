# Unity Asset Store 及其与开源社区的比较

> 原文：<https://dev.to/halileohalilei/unity-asset-store-and-its-comparison-to-open-source-communities-1p15>

在过去的几年里，我在原生 iOS 和 React 原生开发方面都有相当多的开发经验。对开发过程有巨大帮助的是像 npm 和 CocoaPods 这样的集中式包管理器(CPM)的存在，以及主要围绕它们的开源社区。

Unity3D 是最广泛使用的游戏引擎，它也有一个名为 Unity Asset Store (UAS，从现在开始)的包商店，你可以从中挑选和使用第三方包。即使它在特性方面比大多数 CPM 差得多(例如，UAS 不支持锁文件或 CLI)，它仍然完成了工作。

在我看来，UAS 和其他 CPM 的主要区别在于，UAS 允许并实际上鼓励付费套餐，而其他国家则不允许。当然，其他 CPM 中也有需要许可证才能购买的库，但它们是少数，而且 CPM 通常没有对付费包的内置支持。

从我到目前为止的经验来看，我想解释和思考这对创建者、单个开发者和整个社区有什么样的影响。

### 为了造物主

为你在一个包中付出的努力获得报酬，是创作者把东西放到 UAS 的一个巨大激励。我很确定有人靠他们出售的包装谋生(或者至少是部分谋生)。这也给了创建者一种责任感，因此每当有人遇到麻烦或对他们购买的包有疑问时，他们更倾向于伸出援手。就我个人而言，从来没有一个创建者在一天之内不回复我关于我所购买的包的询问。

### 对整个社区来说

开源社区的好处在于，当需要一个库时，几乎总会有人来解决它。当人们使用这些开源库时，他们可以让维护者知道库可能存在的任何问题，与其他开发人员讨论它，或者发送请求来自己解决问题。每个存储库托管服务(例如 GitHub 和 GitLab)都内置了对这种有机反馈机制的支持，这是开源社区的本质。

UAS 没有这种有机的反馈机制。这里有一个评论区，你可以对你买的包发表评论，还有一个关于包的论坛帖子，人们可以在这里讨论和向创建者提问。但是你没有办法自己参与到库的开发过程中，因为付费库是封闭源代码的，你得到的重要部分是一个. dll 文件。你最好的办法是让创建者知道你可以使用的特性或者这个库有哪些缺陷，然后等待他/她来处理它们。此外，与开源项目相比，创建者更有可能没有时间、意愿和/或能力来解决您所面临的问题。

这导致 Unity 的高质量库数量减少，我认为这是个问题。这并不可怕，但是如果有一个更活跃的社区可以一起工作，情况会好得多。

### 对于个人开发者来说

当我们可以拥有的时候，我们总是想要免费的东西。知道了这一点，UAS 的创作者几乎总是有两个版本的软件包:一个是免费版本，有软件包提供的功能子集，另一个是付费版本，有所有的功能。通过这种方式，你可以使用基本的功能，并通过试用来看看付费软件是否值得。然后，您可以购买这个包并在您的项目中使用它。如果你有钱的话。

我个人在购买包裹时从未遇到过任何财务困难，因为我工作的公司会支付费用。然而，我毫不怀疑这对独立开发者来说是一个负担，他们没有足够的资金或者刚刚开始一个新项目。这些套餐通常并不贵(尽管如果你生活在一个汇率疯狂的国家，它们可能会贵)，但它们加在一起。我知道这是一个更深入的话题，可能会引发资本主义与共产主义的激烈讨论，所以我不做任何断言，只是列出事实。

### 结论

自从我开始与 Unity3D 合作以来，UAS 是否应该更像其他 CPM 一直是我脑海中的一个想法。我仍然没有答案，也不相信一种模式优于另一种，尽管我更倾向于开源社区的想法。在做出任何大胆的主张之前，我想知道其他开发者对此的看法。
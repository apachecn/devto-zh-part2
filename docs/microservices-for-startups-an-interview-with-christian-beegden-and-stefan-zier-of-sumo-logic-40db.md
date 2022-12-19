# 创业公司的微服务:对 Sumo Logic 的克里斯蒂安·比登和斯蒂芬·齐尔的采访

> 原文：<https://dev.to/jakelumetta/microservices-for-startups-an-interview-with-christian-beegden-and-stefan-zier-of-sumo-logic-40db>

*这次采访是为我们的[创业微服务](https://buttercms.com/books/microservices-for-startups/)电子书而做的。一定要去看看关于微服务的实用建议。感谢 Christian 和 Stefan 的时间和投入！*

克里斯蒂安·比格登是[相扑逻辑](https://www.sumologic.com/)的首席技术官。[相扑的首席建筑师 Stefan Zier](https://twitter.com/stefanzier?lang=en) 参加了这次采访。Sumo Logic 是一项云原生服务，是世界上最强大的机器数据分析服务之一。

就背景而言，你的工程团队有多大？您是否正在使用微服务，能否概述一下您是如何使用它们的？

工程团队大约有 100 人，其中三分之二在编写代码。Sumo 背后的想法是摆脱通过企业软件解决日志管理，将产品转变为服务。在开始 Sumo Logic 之前的近 10 年时间里，我们一直在努力解决日志管理企业软件的扩展问题，仅仅以每秒 5，000-10，000 个事件的速度处理日志。

当我们开始 Sumo Logic 时，我们甚至没有讨论是否要将系统构建为多租户服务——这是显而易见的。

最终，你拥有了你能买到的最大的甲骨文盒子，之后它就不会再快了。显然，我们需要构建一个横向扩展的系统。很快，我们还了解了扩展的其他方面，例如分而治之，将客户划分到多个集群。

我们还知道，系统中会有处理数据接收的部分、处理索引的部分以及处理查询、缓存和聚合数据的部分。很明显，这些只是独立运行的小应用程序，我们会以某种方式将它们捆绑在一起。很明显，它不能在一个盒子上工作。

围绕服务的复杂性和粒度，我们经历了大量痛苦和讨论。我记得在 2012 年和 2013 年，斯特凡和我进行了激烈但富有建设性的讨论。也许我们建立了一个过于复杂的系统？你甚至不能在笔记本电脑上运行它了。回想起来，我认为它对我们大多数人来说都很成功。

**你是从单体开始，后来采用微服务的吗？**

长话短说，这不是一个“我们有一块巨石，我们把它打碎了”的故事。这是一个“总是微服务，总是在 AWS 中”的故事。

作为一个团队/工程组织，你是如何处理微服务这个话题的？

我们之前已经在其他地方构建了一个类似的应用程序，并且很好地理解了它的基本细节。最初，我们没有把应用程序分解成微服务。

我们没有充分认识到数据重力和数据移动以及将接收与搜索路径分开的一些影响。不同的输入驱动不同的缩放行为。我们大概花了一两年的时间，才被一些东西吸引，这些东西最终开始工作并扩大规模。

为了应对采用微服务，您是否改变了团队的组织或运营方式？

我们目前采用了一种叫做产品开发单位(PDU)的模式。它们是围绕这些微服务和后端开发人员的一个非常强大的容器。UI 开发人员漂浮在 PDU 之间。通常，PDU 还附带一个产品经理。

UI 开发人员和质量工程团队是浮动的，但是产品经理和后端开发人员是永久地依附于 PDU 的。并且每个 PDU 拥有一些微服务。他们类似于亚马逊喜欢谈论的两个披萨大小的团队。

PDU 是围绕代码和操作知识的相当强大的容器，当你需要推出横切变化时，它有缺点。我们最近不得不做的一些事情的例子是从 Java 7 到 Java 8——我有点不好意思承认这是最近的事情。或者迁移到 VPC 的过程。让所有的 PDU 为他们的 it 服务执行横切变更并不容易。

随着时间的推移，我们的组织方式已经发生了变化，人数也发生了变化。我们刚开始的时候，是四五个开发者到 20 多个微服务。现在是 80 到 40 或者 50 的微服务。

最初，每个服务归一个人所有是没有意义的。甚至是一个团队，每个人都拥有一切。但是最终随着团队的成长，我们将服务分成了几个团队。不是个人，是团队。

真正重要的一点是，软件开发人员对软件拥有完全的所有权。换句话说，他们不仅构建软件，还运行软件，并对整个生命周期负责。

他们也需要被给予足够的自由去这样做。这是整个自由和责任的事情。如果他们要成为被软件唤醒的人，他们还需要尽可能在一些基本的指导方针下做出关于如何构建软件的决定。

这确实是一种联邦文化。你必须有一个系统，在这个系统中，多个独立的单元为了更大的目标而走到一起。这在某种程度上限制了这些单位的独立性，他们必须同意存在某种形式的联邦政府。但是在更小的群体中，他们可以在更高层次上建立的指导方针下尽可能多地自己做决定。这是看待它的一种方式。

你如何确定服务边界？

那是一个棘手的问题。我一直在思考这种分布式架构，它就像更高抽象层次上的面向对象设计。我们从小就被教导面向对象设计，基本的口号一直是“低耦合和高内聚”

这就是你试图看待类以及类、包、模块等之间的交互的方式。在某种程度上，我们现在有了另一种容器。

我记得我是从这个角度来看待这件事的。我们过去是如何找出哪些东西需要放在一个产品包中，哪些东西需要放在一个模块中，然后将它提升到服务。

有些是直觉。拿起一块白板，让我们快速思考系统的主要组件是什么，分解它们，一、二、三，用一串箭头连接组件，开始制作 GitHub repos，然后你就有了一个起点。

我认为领域经验在这种情况下是有帮助的，但是有些事情我们犯了严重的错误。我们最初将数据的索引和搜索分开。从这个角度来看，它应该是相同的模块或相同的服务，因为...可能不是同一个模块，但就不同的群集和数据而言，有些方面分离得太远了...在这些集群之间交换本质上相同的数据是一个非常繁琐的过程。它增加了延迟，对您的架构造成了各种非常、非常、非常严重的影响，我们花了两三年时间才弄清楚这个初始决策对架构核心部分的影响有多大。

你的团队内部的讨论是怎样的？你能举些例子吗？

我们开始时，每个微服务都有一个超级硬的边界。我记得我对此非常坚定。我们对所有的东西都有单独的回购，因为我被人们烧得够呛——即使在我们只有一个应用程序的旧世界——人们甚至不遵守关于什么应该放入哪个包以及哪个包不应该调用其他包的基本约定。

为了保持低耦合，我对此很激进。因此，这些东西之间的物理边界，独立的回购，一切都只是通过消息和总线交谈。我们最终以 mono repo 结束，并且在许多地方还有基于请求/响应的 API。我想我们现在有多少个模块？两百多。实际上，异步消息传递让很多人掉了很多头发。

**您从规模估算服务中学到了什么？**

一次性升级所有服务不是个好主意。曾经有一段时间，我们部署了几个星期，看到有些东西偏离了轨道，就退回去，重新开始。部署，看到另一件事出了轨，滚回来，回到制图板。在某个时候，我们连续这样做了三、四、五周，最终我们意识到这太荒谬了。我提到过我们真的很喜欢用头撞墙吗？

那时，我们可能已经有了 20 多项服务。这个团队大概有 15 到 20 人。另一种选择是提供一项又一项服务，这似乎同样疯狂。

如何升级一项服务，重启它，确保它正常运行，升级下一项服务，重启，确保它正常运行，并在两个小时的维护窗口内做 25 次或更多次？也不可能。

所以我们在中间着陆。我们发明了一个概念，我们称之为“组装组”，基本上是 25 个服务的较小分组。两个、三个、四个、五个、六个一起升级的服务。

**微服务对你的开发过程有什么影响？您的运营和部署流程？出现了哪些挑战，你是如何解决的？你能举些例子吗？**

我们意识到扩展开发人员入职是高度杠杆化的。过去，我们在这方面做得不太好，一些加入该组织的人有过非常糟糕的经历。

我们现在给人们安排的方式是和一位导师配对，也就是那些已经在这里呆了一段时间，知道他们周围情况的人。我们正在创建一个课程，让他们了解一些他们需要知道的基本知识。

历史上，我们写了很多维基来记录零碎的东西。在这一点上，我强烈反对维基百科。或者至少维基的形式是每个人都可以在任何时候写任何东西。

随着时间的推移，内容管理非常困难。所以我们基本上回到了有一个主持人/策展人。这是非常集中的，所有这一切，它可以感觉有点沉重的手。我认为如果你有像维基百科这样大规模的东西，维基百科是可以工作的。如果你只有一群开发人员，那就没有足够的动力持续更新东西。不幸的是，这就是我们的发现。

我们现在有了一个由我策划的 GitHub wiki。我尽量把它限制在你需要理解的关键概念上，而不是维基最终变成的一切和厨房水槽。每个页面都经过精心策划，其中许多是我自己写的，然后由其他人审阅。

**微服务对您的测试方式有何影响？**

我们通常测试的方式有很多种。一种是我们所说的本地部署。我们在一台笔记本电脑上运行大多数服务，因此您可以获得一个完全运行的系统。目前，16GB 内存的笔记本电脑已经达到了运行的极限。

所以这种方式并不能真正规模化。第二种变化是我们所说的个人部署。这里的每个人都有自己的 AWS 帐户，我们的部署工具是完全自动化的，您可以在大约 10 分钟内在 AWS 中建立一个完整的 Sumo 逻辑实例。

第三种方式我们称之为顽固，这是我们建立的一个存根模块。顽固让您编写微服务的存根，表现得好像它们是真正的服务，并在我们的服务发现中宣传它们自己，好像它们是真正的服务。但它们只是一种虚拟的模仿，做一些你可以控制的事情。这比运行所有这些服务要轻便得多。

例如，如果你在做搜索组件，你总是需要知道哪些客户存在的服务。您需要知道用户和分区以及所有这些事情的服务，但是您并不真正需要具有所有复杂性和功能的真实版本。你只需要假装这里有一个顾客，这里有一个用户。在这种情况下我们会用固执。

在这方面有什么经验或建议？你能举些例子吗？

我认为测试微服务总体来说非常非常困难，尤其是当你转向持续部署模式时。这甚至不像是人类探索性的测试——比如你什么时候做？因此，我们已经并将继续在集成测试、单元测试方面投入大量资金，如果我们有足够的人来做，我们会做得更多。

**微服务对安全性和控制数据访问有何影响？在这方面有什么经验教训或建议？你能举些例子吗？**

我们明白，为了让人们在云中信任我们，安全必须是首要的和中心的。我们知道，许多客户需要遵从 PCI、HIPAA 以及所有这些标准。我们需要把它设计成从底层就能意识到安全性。

我们的部署工具是模型驱动的，模型理解集群、微服务以及它们如何相互通信。我们可以从该模型中生成一组非常严密的安全控制。

特别是在网络层面，我们可以严格根据对谁与谁对话的理解来生成防火墙规则。从安全角度来看，这也是 AWS 为我们做一些繁重工作的地方之一。

随着时间的推移，我们意识到，从安全角度来看，整个云技术实际上是有利的。你不能手工做任何事情，所以一切都必须自动化。一旦你开始编写脚本并自动完成所有的工作，你会突然发现很有可能默认把所有的事情都捆绑在一起。

这里还有很多其他的东西，包括加密和密钥管理——这就是我们从一开始就坚持多租户原则的原因，这迫使我们投资于设计，而不是用大量的“is ops 问题”来敷衍了事。

最后，安全不仅仅是架构和代码——事实上，还有很多与安全相关的过程。这是我们很快发现的。特别是客户需要看到审计报告这一事实。你利用这一点并将其转化为优势，看看审计在控制方面需要什么，然后对照它进行测试。然后审计员进来，他们再次测试。这当然不是没有痛苦的，但如果认真对待，我们确实认真对待，它建立了相当好的习惯。当然，审计只是一部分，架构是另一部分，然后你还要加上测试、bug 奖金等等。你在整个产品开发组织中推动它，包括所有的开发人员。

再次感谢 Christian 和 Stefan 的时间和投入！这次采访是为我们的[创业微服务](https://buttercms.com/books/microservices-for-startups/)电子书而做的。一定要去看看关于微服务的实用建议。
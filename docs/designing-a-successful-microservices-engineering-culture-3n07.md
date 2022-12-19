# 设计成功的微服务工程文化

> 原文：<https://dev.to/jakelumetta/designing-a-successful-microservices-engineering-culture-3n07>

回到我和 Java 开发人员一起工作的时候，我记得在谁来开发最新、最丰富的特性的问题上，团队内部有一种紧张感。我们的工程领导层已经决定，我们将专门使用 Java 来构建所有新的微服务。

这个决定有很好的理由，但是——我将在本章后面解释——这样一个限制性的决定也带来了一些影响。请注意，在可能的范围内，向团队传达技术决策的 _ 为什么 _ 可以在很大程度上创造一种让人们参与进来的文化。

当谈到围绕微服务组织和管理团队时，平衡团队的情绪、士气和整体文化总是具有挑战性。在大多数情况下，领导层需要平衡团队成员使用新技术的风险与客户和业务本身的需求。

这种困境，以及其他许多类似的困境，让首席技术官们问自己这样的问题:在采用新技术时，我应该给我的团队多大的自由？或许更重要的是，我如何管理我的团队中的总体文化？

和前几章一样，我们向专家寻求一些指导。

## 稳定性 vs 灵活性

假设你雇佣了一名新的初级开发人员。他们可能会对一些全新的新鲜出炉的 JavaScript 框架感到兴奋。几乎 *太过* 新。

虽然该框架取得了一些技术突破，但它可能还没有在生产环境中证明自己，而且它很可能没有很好的支持。首席技术官们面临着艰难的选择，要么为了团队的士气和激情而同意这一举措，要么为了维护公司的需求、保护公司的底线以及在截止日期临近时保持项目稳定而拒绝这一举措。

正确的答案取决于很多不同的因素，这也意味着这里 *就是* 没有正确的答案。

“在考虑技术选择时，我们给予我们的团队和我们自己 100%的自由。我们最终确定了两三项最终不使用的技术，主要是因为不想让我们的部署故事变得复杂，”蜜獾的联合创始人 Benjamin Curtis 在接受我们的采访时说。

“换句话说，在创建微服务时，我们考虑将新的语言和新的方法引入我们的技术堆栈，我们实际上已经在不同的堆栈上部署了生产微服务。[虽然我们通常]坚持使用我们了解的技术，以简化我们的运营堆栈，但我们会定期重新审视这一决定，看看采用新技术是否会带来潜在的性能或可靠性优势，但迄今为止我们尚未做出改变，”柯蒂斯继续说道。

当我 [与 PubNub](https://buttercms.com/blog/microservices-for-startups-an-interview-with-stephen-blum-of-pubnub) 的首席技术官 Stephen Blum 交谈时，他也表达了类似的观点，支持欢迎几乎任何可行的技术:

“我们对此完全开放。Blum 说:“我们希望继续推进可用的新开源技术，我们对团队只有几个非常公平的限制:必须在容器环境中运行，并且必须具有成本效益。”。

另一方面， [的联合创始人达比·弗雷对技术选择采取了更为严格的方法](https://buttercms.com/blog/microservices-for-startups-an-interview-with-darby-frey-of-gamut) 。

“在我的上一家公司，我们有很多服务和一个相当小的团队，而让它成功的主要因素之一，尤其是对于我们的团队规模来说，就是每个应用都是一样的。每一个后端服务都是一个 Ruby 应用，”他解释道。

Frey 告诉我这是如何帮助简化他的团队生活的，就像每个服务一样，“相同的测试框架，相同的数据库后端，相同的后台作业处理工具，等等。一切都是一样的。”

这意味着当工程师在不同的应用程序间切换时，他们不必每次都学习一种新的模式或学习一种不同的语言。所以我们非常清楚并非常严格地保持这种共性，”弗雷说。

与此同时，Frey 对开发者想要引入一种新语言的想法表示同情，承认他“喜欢尝试新事物的想法”。然而，他觉得弊大于利。

“多语言架构会增加开发和维护成本。如果一切都一样，您可以专注于业务价值和业务特性，而不必过于局限于服务的运营方式。我不认为每个人都喜欢这个决定，但当一天结束时，他们不得不在周末或半夜修理东西，他们会很感激，”弗雷说。

## 给每个团队成员一个茁壮成长的机会

让我们从这一章开始重温我的故事。如果你还记得的话，工程领导者认为 Java 是构建微服务时最好的技术。Java 是高性能的，我们团队中的许多高级人员都精通它，所以这就是我们选择 Java 的原因。然而，并不是团队中的每个人都有 Java 经验。

问题是，我们的团队分成了两个阵营:Java 团队和 JavaScript 团队。随着时间的推移，新的令人兴奋的项目出现了，我们总是用 Java 来完成工作。不久，JavaScript 阵营内部出现了一些烦恼。

“为什么 Java 的人总是去做令人兴奋的新项目，而我们却被留下来做诸如实现第三方分析工具之类的普通前端任务？我们也想要一个令人兴奋的大项目！”

像大多数裂缝一样，它开始很小，但随着时间的推移变得越来越严重。

我从那次经历中得到的教训是，在为您的微服务选择事实上的技术堆栈时，以及在调整您给团队挑选工具的自由度时，要考虑到您团队的专业知识和偏好的技术。

当然，你需要有一些结构，但是如果你限制太多，或者更糟糕的是，无视团队成员用不同技术创新的愿望，你可能会有自己的裂痕需要管理。

因此，仔细评估你的团队，并想出一个让团队中每个人都有能力的计划。这样，你团队的每个部分都可以参与到主要项目中，可以说，没有人会觉得他们被留在了板凳上。

## 团队组织的问题

你的团队结构也将影响你的微服务工程文化——或好或坏。

例如，软件工程师通常在将代码发送给运营团队之前编写代码，运营团队再将代码部署到服务器上。但是当事情破裂时(而事情 *总是* 破裂！)，发生内部冲突。

因为运营工程师自己不写代码，所以在问题刚出现的时候，他们很少能理解问题。因此，他们必须与编写代码的人——软件工程师——取得联系。因此，从一开始，您就有一个中间人在问题和可以解决问题的团队之间传递消息。

更复杂的是，因为软件工程师不参与操作，他们通常不能完全理解他们的代码如何影响平台的整体操作。只有当运营工程师抱怨时，他们才知道任何问题。如你所见，这是一段注定会不断冲突的关系。

解决这个问题的一个方法是效仿网飞和亚马逊，这两家公司都支持分权治理。詹姆斯·刘易斯和马丁·福勒，两位软件开发思想领袖，通过一篇冗长的博客文章 展示了他们的思想 [。根据他们的观点，分散治理是微服务团队组织的发展方向。](https://martinfowler.com/articles/microservices.html#ProductsNotProjects)

“集中治理的后果之一是倾向于在单一技术平台上实现标准化。经验表明，这种方法是有局限性的——不是每个问题都是钉子，也不是每个解决方案都是锤子，”文章写道。

“也许去中心化治理的顶点是亚马逊推广的‘建立它，运行它’的理念。团队对他们构建的软件的所有方面负责，包括 24/7 运行软件，”它继续说道。

Lewis 和 Fowler 写道，网飞是另一家推动开发团队承担更高责任的公司。他们假设，因为他们将负责并在以后出现任何问题时被调用，所以在开发和测试阶段将更加小心，以确保每个微服务都处于良好状态。

他们总结道:“这些想法与传统的中央集权治理模式相去甚远。”。

### 高自由、高责任的概念

在我采访 Sumo Logic 的首席技术官 Christian Beedgen 和首席架构师 Stefan Zier 时，他们对这个话题进行了详细的阐述，进一步强调了这样一个观点，即如果你要让开发者自由选择他们的技术，就必须附带高度的责任感。

“无论是谁开发的，都要对软件拥有完全的所有权，这一点非常重要。换句话说，他们不仅构建软件，还运行软件，并对整个生命周期负责，”他们说。

他们继续解释说，应该建立一个类似于联邦政府系统的系统，通过加强责任来帮助控制这些自由。

“[你需要]一种真正的联邦文化。你必须有一个系统，在这个系统中，多个独立的团队可以为了更大的目标而走到一起。这在某种程度上限制了这些单位的独立性，因为它们必须同意潜在地存在某种形式的联邦政府。但在那些较小的群体中，他们可以在更高层次上建立的指导原则范围内自己做尽可能多的决定，”他说。

分散的、联邦的，或者无论你想怎么描述，看起来都是构建微服务团队的一个有吸引力的方法。这是一种给每个团队和每个团队成员他们想要的自由的方法——没有给任何人将整个项目撕裂的自由。

但是并不是每个人都同意。

### 周末谁会被传呼？

你看，一个分散的系统意味着每个分散的团队负责一项服务或一组服务。但是这也产生了一个问题；筒仓。

这也是 Darby Frey,“诚实领导”的联合创始人不支持分权治理概念的原因之一。

“单个团队负责一项特定服务的模式在微服务架构中很常见。我们不这么做，有几个原因。主要的商业原因是，我们希望团队不负责特定的代码，而是负责面向客户的特性。一个团队可能负责订单处理，因此会涉及多个代码库，但业务的最终结果是有一个团队端到端地拥有整个事情，因此事情失败的可能性更小，”Frey 解释道。

他接着说，另一个主要原因是开发商可以获得整个项目的更多所有权

弗雷说:“他们实际上可以从整体上考虑这个项目。”。

Nathan Peck，亚马逊网络服务的容器服务开发者倡导者， [更深入地解释了这个问题](https://medium.com/@nathankpeck/microservice-principles-decentralized-governance-4cdbde2ff6ca) 。本质上，当你将软件工程师和操作工程师分开时，无论何时代码出现问题，你都会让你的团队的日子更难过——这对最终用户来说也是坏消息。

但是我是这么想的；去中心化需要导致分离和孤岛化吗？

Peck 继续解释说，他的解决方案在于 DevOps，这是一种旨在通过拉近这两个团队的距离、加强团队文化和沟通来收紧反馈回路的模式。Peck 将此描述为“你构建它，你运行它”的方法。

然而，这并不意味着团队必须孤立或远离某些任务的参与，就像弗雷建议的那样。

佩克写道:“去中心化治理最有效的方法之一是建立一种‘开发’的心态。”。“[使用这种方法]，工程师参与软件管道的所有部分:编写代码、构建代码、部署最终产品，以及在生产中操作和监控它。DevOps 的方式与旧的将开发团队与运营团队分开的模式形成了对比，它让开发团队将代码“越过墙”传送给运营团队，然后运营团队负责运行和维护它。”

DevOps，正如 [军械库首席技术官 Isaac Mosquera 解释的](https://buttercms.com/blog/microservices-for-startups-an-interview-with-isaac-mosquera-of-armory) ，是一个敏捷软件开发框架和文化，它正在获得牵引力，这要归功于——嗯，差不多是 Peck 所说的一切。

有趣的是，莫斯克拉觉得这种做法其实是在公然对抗 [康威定律](https://en.wikipedia.org/wiki/Conway%27s_law) :

“设计系统的组织...被限制生产这些组织的通信结构的复制品。”— M .康威

“现在软件架构驱动通信，而不是通信驱动软件设计。不仅团队以不同的方式运作和组织，而且需要一套新的工具和流程来支持这种类型的架构，即 DevOps，”Mosquera 解释道。

工程 SparkPost 副总裁克里斯·麦克法登举了一个有趣的例子，或许值得效仿。在 SparkPost，你会发现分散治理——但你不会发现一个团队一项服务的文化。

开发这些微服务的团队最初是一个团队，但现在他们分成了三个团队，隶属于同一个更大的团队。麦克法登说:“每个团队在某些领域和某些专业知识方面都有一定程度的责任，但这些服务的所有权并不局限于其中任何一个团队。

麦克法登解释说，这种方法允许任何团队从事任何工作，从新功能到缺陷修复，再到与这些服务相关的生产问题。这是完全灵活的，看不到筒仓。

“这让[团队]在新产品开发方面更加灵活，因为你不会受到太多的限制，这是基于我们作为公司和工程团队的规模。我们真的需要保留一些灵活性，”他继续说道。

然而，规模在这里可能很重要，因为麦克法登承认，如果 SparkPost 大得多，“那么让一个更大的团队拥有其中一个微服务会更有意义。”

“我认为，对这些服务承担更广泛的责任会更好，这会给你更多的灵活性。至少在这个时候这对我们有用，我们是一个组织，”他说。

另一方面，Pusher 的工程副总裁 Sam Stagg 采用了 Conway 的方法——选择让团队在项目的不同领域开展工作:

“我们试图组织我们的团队去探索康威定律。因此，我们有一个小团队为平台构建核心共享服务，而支持特定产品的服务由构建产品的团队来构建，”Stagg 说。

## 成功的微服务工程文化需要微妙的平衡

谈到技术，自由和责任似乎是最有回报的途径。拥有不同技术偏好的团队成员会来来去去，而新的挑战可能需要你放弃以前对你很有用的技术。软件开发是不断变化的，所以当新的设备、技术和客户出现时，你需要不断地平衡你的团队的需求。

至于构建你的团队，一种分散的、非孤立的方法，利用 DevOps，灌输“你构建它，你运行它”的思想，似乎很受欢迎，尽管也存在其他的思想流派。像往常一样，你将不得不进行试验，看看什么最适合你的团队。

这里简单回顾一下如何确保你的团队文化与微服务架构很好地融合:

*   **保持可持续性，同时保持灵活性:** 平衡可持续性，不要忘记灵活性，以及当合适的机会到来时，你的团队需要创新。然而，对于如何实现这种平衡，存在明显的意见分歧。
*   给予平等的机会: 不要偏袒团队中的某一部分人。如果你要施加限制，确保它不会从一开始就疏远团队成员。思考你的产品路线图是如何形成的，并预测它将如何构建，以及谁来做这项工作。
*   组织你的团队要敏捷，但要有责任心: 分散治理和敏捷开发是当今的主流，这是有充分理由的，但不要忘记在每个团队中树立责任感。

Web 组件是微前端的核心概念:一种设计类似于微服务架构的复杂前端应用程序的新方法。使用微服务架构，我们可以使用 [Web 组件来创建微应用](https://buttercms.com/blog/using-web-components-with-buttercms)，每个应用都有特定的任务。查看[我们的帖子](https://buttercms.com/blog/using-web-components-with-buttercms)了解更多

*感谢以下个人对本章的贡献:* *[本·柯蒂斯](https://twitter.com/stympy?lang=en)，[斯蒂芬·布鲁姆](https://twitter.com/stephenlb?lang=en)，[达比·弗雷](https://twitter.com/darbyfrey)，[克里斯蒂安·比根](https://twitter.com/raychaser)，[斯蒂芬·齐尔](https://twitter.com/stefanzier)，[艾萨克·莫斯克拉](https://twitter.com/imosquera)，[克里斯·麦克法登](https://twitter.com/cristoirmac)，[萨姆·斯塔格](https://twitter.com/swstagg)，以及[塞拉·斯特林](http://www.linkedin.com/in/sierrasterling)。*

这是针对创业公司 的 [*微服务的一部分。如果你喜欢，请分享！*](https://dev.to/books/microservices-for-startups)

### 享受本章？不要错过下一个。
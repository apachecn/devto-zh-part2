# 持续交付有助于建立学习文化的 7 种方式

> 原文：<https://dev.to/markoa/7-ways-continuous-delivery-helps-build-a-culture-of-learning-11o5>

持续交付的核心是一个快速反馈循环，它可以立即向开发人员展示他们工作的效果。错误很快被发现并修复，而有益的更改可以发布并部署给客户，而不必等待遥远的将来的发布日期。这种快速反馈有助于建立一种学习和责任的组织文化。

基础是[持续集成](https://semaphoreci.com/community/tutorials/continuous-integration):每当开发人员向版本控制提交新的变更时，快速自动化测试在类似生产的环境中运行，以确保代码和系统作为一个整体安全地部署给用户。在许多情况下，如果测试已经通过，就会自动触发部署。如果没有，团队知道系统处于可部署状态，并根据他们的时间表手动启动部署。

大多数情况下，快速反馈循环给了开发人员继续工作的许可，或者继续下一个任务。如果我们能够在几分钟内验证和部署我们的变更，我们就保持了流程的状态，并且能够继续非常有效地工作。

然后，有时反馈回路会产生一些需要采取行动的新信息。例如，我们可能会收到错误率上升的报告，或者在我们对购物车设计进行了更改后，观察到用户参与度的变化。因为连续交付支持频繁的系统更新，所以我们所做的更改很小，反馈循环被设置为给我们小块的信息。在部署了几个小时的工作后得到的即时反馈比在三个月的全力工作后得到的缓慢反馈更容易理解。

以下是通过持续交付学习的一些具体例子:

1)持续集成引导开发人员快速解决问题。他们**及时了解问题**——而不是在几天或几周后，当 QA 最终发现问题并且代码在开发人员的脑海中不再新鲜时。

2) **修复很小，它们的成果很容易记录**。好的文档有助于建立组织知识。当开发人员知道过去出了什么问题时，类似的问题可以更快地被发现，或者完全避免。

3)由于需要清理的重大失败较少，组织可以将精力集中在产品功能开发和内部流程的实验和**度量驱动的学习**上。

4)功能标志，有时也称为功能切换，允许我们在生产中迭代地构建复杂的新功能，并通过早期与客户交谈来验证它们。这个过程，有时被称为**持续产品发现**，帮助我们避免投资建造没人想要的昂贵东西。我们可以专注于对客户有价值的特性，并对它们进行改进，直到满足客户需求和业务目标。

5) **不断的实验**导致不断的学习。开发人员在公司内部的“展示和讲述”活动和演示中分享他们所学到的东西，这提高了整个团队的技能，并鼓励进一步的分享。在这种环境下，同伴们通常会互相推动。

6)在连续交付中，**每个人都拥有他们工作的质量**。每个开发人员都采用测试驱动开发，学习如何使用日志记录，并为他们拥有的组件建立监控指标。代码审查是每个拉取请求的标准实践。当协作成为第二天性时，知识就会在同事之间有机地传递。因此，每个人都部署到生产中，没有遥远的权威锁定知识和过程。

7)通过小的改变和分散的所有权，人们高度协作，团队成员相互信任。因此，当出现问题和停机时，团队倾向于将其视为一个学习和改进的机会，而不是事后指责对方。

孤立开发的大型项目可能会受到技术障碍和长时间周转的阻碍，即使部署了，如果没有反馈和额外的修复，它们也可能无法满足用户的需求。一个连续的交付系统支持快速的、迭代的软件开发——但是只有当我们很好地使用它的时候。我们有责任理解每一次迭代都是一次学习的机会，并将这种学习应用到我们的工作中。

*最初发布于[旗语博客](https://semaphoreci.com/blog/2018/02/14/7-ways-continuous-delivery-helps-build-culture-of-learning.html)。[信号量](https://semaphoreci.com)是基于云端的 CI/CD 服务*。
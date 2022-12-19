# 接管现有 Rails 应用的 7 个步骤(在你写一行代码之前)

> 原文：<https://dev.to/planetargon/7-steps-to-take-over-an-existing-rails-app-before-you-write-a-line-of-code-219g>

[![How to take over an existing Ruby on Rails app](../Images/c9b1ef104faa5bd42a15047b01ad367c.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--DTDWkEu0--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://s3-us-west-2.amazonaws.com/planetargon-blog/images/2018/0218/7-steps-to-take-over-existing-rails%2Bapp.png)

我们长期维护和开发的大多数 Ruby on Rails 应用程序都是继承而来的。我们的客户通常会给我们带来最初由自由职业者、内部开发人员或其他机构开发的应用程序。

在十几年的应用程序工作中，我相信我们在改进和发展现有的 Ruby on Rails 应用程序时做得最好。

Ruby on Rails 社区最好的一个方面是，当遵循约定时，我们的团队能够相当快地进入现有的代码库，并对事物如何组合有所了解。

但是继承一个“遗留”Rails 应用程序需要在输入一行代码之前完成一些步骤。如果不花时间探索和了解应用程序当前的架构和工作方式，就不可能准确估计完成任务所需的时间，更不用说实际完成任务本身了。

那么，在我们开始处理现有的 Rails 应用程序之前，我们的流程是什么样的呢？

以下是我们在继承遗留的 Ruby on Rails 应用程序时采取的七个步骤，为什么它们很重要，以及这些过程如何支持我们改进客户产品的能力。

## 第一步。让利益相关者解释他们的业务

在与潜在客户的初次通话中，我们通过一系列问题来做到这一点。根据公司的不同，我们会遇到从营销经理到设计师到技术总监的任何人。以下是我们在最初几次谈话中会问到的一些问题。

*   他们的业务是做什么的？
*   他们从事什么行业？
*   他们最大的竞争对手是谁？
*   他们是如何做决定的？
*   他们会如何描述他们的公司文化？
*   该应用程序如何融入他们的软件生态系统？
*   他们的客户会与它互动吗？
*   第三方厂商/合作伙伴需要与之交互吗？
*   和/或这主要是为了幕后操作？
*   他们是否在应用程序中开发了需要向外部和/或内部工具公开的 API？如果是这样，谁依赖这些？
*   该应用程序是否有助于任何金融交易？
*   此应用程序是否存储任何极其敏感的数据？(即健康记录、账单信息、个人数据等。)
*   它是任务关键型的吗？如果项目在周六晚上中途停止，会对他们的业务产生什么影响？

## 第二步:什么没用？

每个拥有现有应用程序的客户都会向我们讲述他们的应用程序运行良好(或不太好)的故事。

*   **他们的应用程序中有哪些地方*看起来*很脆弱？**有没有看起来反复断裂、修复、再次断裂、修补、断裂、冲洗、起泡和重复的零件？这可能会突出代码库中可能非常复杂和/或测试不足的区域。

*   有没有开发出来却没人使用的功能？这是一个可以删除和/或需要改进以变得有用的领域吗？

*   **他们害怕处理应用程序的哪些方面？**他们在抱怨应用程序的哪些部分，或者他们一直在开玩笑说要处理哪些部分？

*   **他们最终为应用程序的哪些领域创造了“创造性”的解决方案？**这可能暗示了一组设计不佳的特性——也许是某个方面需要改进。

我们将此记录下来以供将来参考。我们工作的一个重要方面就是倾听。这些棘手的问题目前可能不在他们的优先列表的最上面——但是在某个时候，这些领域在将来会很好地提出来。

四个月后，问一个类似*的问题:“嗨，Sarah——导入工具对你的团队来说仍然是一个棘手的问题吗？我们是否应该在不久的将来对此进行研究？”*

人类有一种有趣的方式来接受和习惯他们软件中的烦恼。我们的立场是，好的伴侣应该倾听这一点，并想办法让他们的生活变得更好——即使是很小的事情，比如让文本框变大一点，这样他们就不必在文本框中键入几个段落，或者清理尴尬的导航模式。有时候，我们从最小的解决方案中得到最大的感谢。

## 第三步。浏览应用程序

在我们开始深入研究代码库之前，我们将安排一次面对面或屏幕共享会议，让我们的新客户带我们浏览他们的 web 应用程序。如果可能的话，我们会记录这次会议，以便我们可以回去参考和/或让其他团队成员参与项目。

这对于联系回他们的用户角色和业务目标非常有帮助。由于我们没有时间(也没有认知能力去记忆)去深入应用程序的每一个角落，我们通常会要求他们演示 2-3 个任务，每个角色都需要可靠地与之交互。

在此过程中，我们将记录他们的用户角色，在 Confluence 中记录这些角色，并确定如果我们对应用程序有进一步的问题，哪些利益相关者是最好的解决方法。例如，“Maggie 是他们报告工具的好联系人”，“Geoffrey 是他们数据导入功能的好联系人”，“Lindsay 似乎最了解他们的 API 功能”，等等。

我们的目标是为我们的团队提供有用的信息，以便他们能够联系到合适的人。

## 第四步。给我们看看你的积压

在这里，我们要求查看团队现有的任何积压文档。我们已经看到客户通过访问他们现有的 Pivotal Tracker 帐户、JIRA 看板、巨大的电子表格来联系我们(我们看到这种情况的频率远远超过您的想象！)，电子邮件中的请求列表，或概述完整用户故事和模型的正式 PDF 文档。

通常情况下，我们会将客户转移到我们自己的 JIRA 云帐户，并帮助他们导入和/或添加票证，以便我们开始进行优先排序。虽然有些客户可能想保持他们的历史完整，但将未来的待办事项迁移到一个内聚的系统中是最有效的前进路线。以下是我们喜欢 JIRA 的几件事。

## 第五步。记录所有的事情！

[![All the rails things!](../Images/d8149d19d7c7b26d98b45ec000210e16.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--J6Lu6oM_--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://s3-us-west-2.amazonaws.com/planetargon-blog/images/2018/0218/all-the-rails-things.jpg)

在我们开始编码之前，我们需要了解一下情况。当我们对他们的应用进行正式的[代码审计/审查](https://www.planetargon.com/services/ruby-on-rails-code-audit)时，其中的一些会被询问和确定。其他问题我们将在早期会议中提出。

这里是我们将记录的一些应用程序细节。

*   是否托管在 Github、Bitbucket 等上。？
*   我们的开发人员需要与 VPN 交互吗？我们处理那里的任何访问/许可的主要联系人是谁？
*   他们有任何架构文档、模型等吗？
*   应用程序托管在哪里？(Heroku、AWS、Rackspace、EngineYard、内部服务器等。？)
*   他们有暂存环境吗？这些与其生产环境的匹配程度如何？
*   应用程序是否运行在任何 cdn(Akamai、CloudFlare、CloudFront 等)上。)
*   他们是否有任何性能监控工具(New Relic、Skylight、Scout 等)？)
*   他们是否使用了任何自动化的错误报告工具(Bugsnag、Airbrake、Honeybadger 等)。)
*   他们的文档记录了他们现有的开发人员是如何处理部署的吗？

## 第六步:审计 Ruby on Rails 代码库

我们坚信，通过对现有应用程序进行彻底的代码审计来开始新的合作伙伴关系，是一个坚实的良好开端。当没有紧迫的时间表来开始新的开发时，我们将从对 Rails 应用程序的代码库进行统一审计开始开发。

该审核为我们提供了更多关于潜在的安全和稳定性问题的信息，这些问题以前可能没有被发现。它还记录了应用程序的结构。经过代码审计后，我们对应用程序的了解比没有审计时要多得多——通常，客户也会对他们的应用程序有很多了解。

我们将保持简短，因为我们以前已经广泛地讨论过代码审计。你可以阅读[我们在审计 Rails 应用程序时采取的八个步骤](https://blog.planetargon.com/entries/ruby-on-rails-code-audits-8-steps-to-review-your-app)来获得更多信息。

## 第七步:开始编码(先从小事开始)

在我们深入新客户需要的任何大的更新之前，我们总是试图确定一个小的更新(也就是说，我们可以在几个小时内编码和测试)。这里的目的是通过我们的沟通工具进行试运行，进行更新，获得客户的批准，推向生产，获得最终批准并关闭请求。

我们倾向于发现服务器访问、团队之间的通信方面的小问题，和/或需要对我们的工具提供更多的培训。在我们共同建立了一些信心之后，我们就能够开始处理更大的项目了。

在我看来，这种轻松融入 it 的方法在早期非常重要。如果客户有一个紧急的 bug 出现在我们的关系中几天——而我们还没有向他们展示(也没有向我们自己展示！)我们可以成功地向他们的环境推送更新，但我们可能无法足够快地对问题做出响应。

**结束语**

在这一点上，我们应该对我们的新(对我们来说)客户的业务是如何运作的，他们现有的 Rails web 应用程序是如何适应的，它为他们提供了什么，它有多重要，它托管在哪里，以及我们需要注意什么技术债务有一个大致的概念。从这里，我们可以开始深入他们的待办事项，检查他们的特性请求和修复。

* * *

您是否有希望重建、重新设计、扩展或更新的现有 Rails 应用程序？

我们很乐意与您讨论您的项目挑战和目标。单击下面的链接，安排与我们的通话。
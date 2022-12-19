# 是时候升级代码审查了

> 原文：<https://dev.to/lhuria94/time-to-level-up-code-reviews-g2>

这是我上一篇关于代码标准的博文的后续。

因此，成为代码审查过程的一部分对我来说非常重要，相信我，我对此非常认真。这不仅是团队的需要，也是个人学习的需要。

代码审查对于知识转移和避免犯小的/常见的错误是非常重要的，当然也是维护整个开发团队的最佳实践的关键。让我们以我的团队为例:我们团队中大约有 12-15 名开发人员，他们都在编写需要评审的代码。所以基本上这是一大堆代码！

## 为什么很重要

将代码推向生产很容易。谁都可以做，对吧？我们所关心的是我们将部署哪些组件。

代码可以是完整的，也可以是让一切都分崩离析的一部分。为了保持高代码质量，我们都需要进行同行代码评审。这没有什么不好的，我们都在同一个团队，我们有一个共同的目标，那就是提供最高质量的产品。

你一定在想，值得吗？没有吗？什么事？

当然，没有将代码评审集成到项目中会导致大问题。你可能很久以前就听说过那场灾难:给你。

这一事件的发生有很多原因，其中一个原因是缺乏同行代码审查。在审查他们的源代码后，他们发现——可能的位翻转、会禁用故障保险的任务死亡、内存损坏、单点故障、对堆栈溢出和缓冲区溢出的保护不足、单故障包容区域、数千个全局变量。流程和产品中的缺陷清单很长。

## 我们如何卷东西

**一般开发流程**

[![Dev process](../Images/9f8e55b70ffda10734a71e1f6b7f396e.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--nBxLRZEq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://lhuria94.github.io/assets/img/2017-10-16-time-to-level-up-code-reviews/dev-process.png)

仅供参考；)

*   绿线:确定通过状态。
*   红线:确定故障状态。

这是我们在大多数项目中遵循的一般流程，当然，栏目可能会根据不同的方面、客户和项目而有所不同。希望非常清楚😓，如果不是我尽力了！！哈哈的笑😄

**Github 代码评审流程**

[![Github project](../Images/f8bd14d1cb1539f2c7132a6cf626a9e2.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--uXk5qD3I--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://lhuria94.github.io/assets/img/2017-10-16-time-to-level-up-code-reviews/github-project.png)

现在，在 GitHub 上只需点击几下鼠标，就可以轻松维护您的代码评审流程(这真的很棒！).我们可以在回购协议上创建新项目，并按照我们的意愿使用它。

一般来说，我们有大约四列，通常就足够了:

*   准备好接受审查:如果您的代码已经准备好接受审查，您可以将卡片(Pull requests)添加到这个列中。
*   在审查中:现在代码审查者的责任是将卡片移动到“在审查中”列，以便它在分支上得到更新，并且相关的开发人员知道他/她的标签当前正在被审查。
*   变更请求:同样，如果审查没有通过标准，代码审查者有责任将卡片移到这一列。然后，相关开发人员将进行所需的修复，并需要将票证推回“准备审查”。
*   关闭/完成:如果卡片位于“关闭”栏，这意味着 PR 已经通过了它应该通过的标准。

**复习时要找什么**

在审查代码时，我们会考虑某些方面，其中一些方面如下:

*   与 Drupal 标准相关的最佳实践。可以在这里找到[。](https://www.drupal.org/docs/develop/standards)
*   JS 特定编码标准。可以在这里找到[。](https://www.drupal.org/docs/develop/standards/javascript/javascript-coding-standards)
*   SCSS 特定编码标准。可以在这里找到[。](https://www.drupal.org/docs/develop/standards/css/css-coding-standards)
*   任何增加技术债务的开发。例如，选择一个简单的解决方案会使以后实现更改变得更加困难。
*   安全问题
*   可能给现有解决方案带来性能问题/威胁的潜在影响
*   正在开发的解决方案已经存在于代码库中，可以重复使用。
*   一般标准，如格式，林挺问题，评论，命名模式等。

**谁负责**

对于谁将负责代码审查过程，我们几乎没有制定什么指导方针。以下是要点:

*   每张票将有一名高级和一名初级代码评审员。
*   审查将在每日站立后立即进行。(取决于需要多长时间。)
*   一个人将在一天内至少审核一张票(如果板上分配了任何票)
*   根据最新更新，门票应该在各自的栏中。(代码审查者和开发人员的责任)
*   如果高级代码评审员有任何反馈，初级代码评审员有责任看看他/她错过了什么。

**确保流程得到遵守**

我们定期回来，观察我们按照设定的流程做得如何，以及是否有任何方法可以改进，以确保它得到遵守，而不是成为任何人工作的负担/阻碍。

根据客户和团队的不同，在不同的平台上清晰地定义和维护流程。我们通常使用 Confluence，并强烈推荐给正在阅读这篇文章的人。

**从错误中学习**

我们维护了一个代码反馈表，其中提到了我们需要避免的常见错误。每个人都可以从团队中访问，并可以添加我们可以改进的地方，实现特定功能的新技术，严格避免特定的编码模式。

> 我们的目标是
> 增强个人的学习，成为更好的程序员。
> 提高代码库的质量，随着代码的增长，管理变得越来越复杂。
> 不仅仅是数量，而是质量。
> 维护团队纪律，理解意大利面条代码的严重性。

差不多就是这样！在这一点上，我可能没注意到什么。如果你想了解更多或者在这里发表评论，请拨打[lovehuria@gmail.com](//mailto:lovehuria@gmail.com)与我联系，这样我就不用查看邮件了。:D

此处访问原帖[。感谢阅读:)](https://lhuria94.github.io/time-to-level-up-code-reviews/)
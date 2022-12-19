# 为什么同构开发设置不是最好的主意

> 原文：<https://dev.to/antjanus/why-homogenous-dev-setups-arent-the-best-idea-46c8>

我想写一篇简短的博文，解释为什么团队中的开发人员使用不同的设置进行开发很重要。为什么让 Linux 和 windows 用户进入一个由 macOS 主导的领域(特别是 web 开发)很重要。以及为什么远离纯 Chrome 开发很重要。

我想答案在一开始几乎是显而易见的:开发中的多样性意味着你会捕捉到更多跨浏览器/跨平台的 bug。那么为什么不是每个团队都有“配额”或者至少每一步都有一个彻底的 QA 步骤呢？

## 眼下的形势

我在一些开发团队和应用程序中工作过，从拥有六个用户到服务数百万用户的网站。我参加过的几乎每个团队都有几乎相同的开发设置:

1.  最新的 OSX 机器
2.  最新的 Chrome 浏览器
3.  iTerm2 with bash/zsh (fish 很棒，为什么没人用 fish？)
4.  崇高文本或虚拟代码

我总是被迫以不同于其他人的方式设置我的开发环境。我总是有很多个人原因这样做(例如，macOS 界面就是不讨我喜欢，Windows ftw)，但最终的结果总是一样的，我像一个疼痛的拇指一样突出:

1.  最新的 Windows 机器或者可能是 ArchOS
2.  我在轮换时使用的随机浏览器(会是 Opera 吗？还是火狐？还是 Chrome？谁知道呢。)
3.  使用 Bash 或 PowerShell 或 CMD 的 ConEmu 或 TMUX
4.  VSCode、Emacs、VIM 或 Sublime Text

这无疑让我们的运营人员很恼火，因为工具在不同的平台上并不总是以相同的方式运行。

## 我的开发设置教会了我什么

三年前，我开始在一家名为 Landdox 的公司工作。我们有一个为石油和天然气公司做文件/土地管理的应用程序。我们有几个“著名的”“困难的”问题，当我们第一次开始构建应用程序时，我们已经解决了:

1.  最初的配色方案在 MAC 上看起来很棒——在其他每台机器上都难以辨认/无法使用。
2.  按钮上的“加号”总是不对齐——它在 Mac 的 Chrome 上看起来居中，但在 Windows 的 Firefox 或 Chrome 上却不居中。我花了一个星期调试这个，并考虑使用图像...
3.  表单域在 IE 边缘被截断，因此您看不到您键入的文本，也看不到您在选择域中选择的选项。

我们是一家小公司，但事实上，我有一台 Windows 机器，这意味着我能够调试和修复这些问题，更重要的是，当这些问题出现时，我能够注意到它们。

## 工装和新开发人员

工具问题糟透了。当 Docker 在 Mac 机器上完美运行，但在 Linux 或 Windows 上失败时，这很糟糕。但是跨平台解决问题意味着当我们让新的开发人员拥有他们自己的生产设置时，我们不必强迫他们在他们不熟悉的机器、操作系统和编辑器上工作。

这意味着，作为团队中的一名 Windows 开发人员，我为我们团队中至少一名几乎只使用 Windows 的开发人员铺平了道路。他也转而在 Linux 机器上工作，但没关系，我们有 Linux devs 为这种设置铺平了道路。

我只想提一下，几年前当我不得不在 Mac 上工作时，我花了很长时间来适应它。我所依赖的正常应用程序(如 Np++)并不存在，替代性也很差(TextMate？真的吗？).我也不喜欢 UI。我并不讨厌成为 mac 用户，并最终精通了它。

我接受了节奏的改变，但如果我现在正在面试一家公司，他们要求我使用 Mac，我很可能会拒绝他们。事实上，在我职业生涯的早期，我经常这样做。

## 边开发边测试浏览器

由于应用程序中的性能问题，我们偶尔会收到罚单。我们正在运行 AngularJS/Angular hybrid，如果您曾经在处理大量数据的生产应用程序上这样做过，您会知道当两个框架冲突时会出现奇怪的性能问题(“颠簸”是我的描述)。

这种颠簸很容易发现，并且通常出现在不同的浏览器中；然而，也有一些不那么隐蔽的性能瓶颈。我们发现一个只在 IE Edge 上出现的错误，不知何故，只在我的机器上出现(其他使用 Windows 的开发人员还不能重新创建它)。

在我谈到这一点之前，让我详细阐述一下使用您的开发环境作为测试平台的想法。

不是每个团队都有 QA，而且只存在于特定条件下的易变的 bug 很难用常规的 QA 技术来测试或发现。我们采用 e2e 测试，但这些测试在 Cypress 上运行，这意味着它们在类似 Chrome 的环境中运行。

我一直用火狐作为我的主要浏览器。这是一个非常棒的浏览器，开发工具也非常棒——绝对不像开发人员喜欢说的那样是 Chrome 的“次要”浏览器。

对于 Firefox，在我的常规开发过程中，我发现了许多错误和烦恼。我不得不下载一个在浏览器中构建的报告(是的，你可以在浏览器中构建一个 excel 电子表格，而不用访问服务器！)但是文件名的构造方式导致了 Firefox 中的无效文件。

我还注意到了一个奇怪的错误，表单域和其他几个部分会消失。

## 拖到 IE 边缘

那么回到性能问题。我决定将 IE Edge 作为我的首选浏览器，这样我就可以留意这些东西了。我们的客户群在一定程度上使用 Edge，这意味着我会在他们之前发现这些错误。

到目前为止，Edge 向我透露了不少信息:

1.  有一次，我们加载了一个 12mb 的供应商文件...是啊，12mb。它是我们的依赖项的副本，已经被树摇动并捆绑到我们的主应用捆绑包中。只有 Edge 抱怨过
2.  我们的应用在 Edge 上比在 Chrome 或 Firefox 上快得多。不，说真的。太疯狂了。
3.  Edge 的自定义自动填充功能会导致带有`$scope.$watch`的字段发生混乱，并在此过程中更新其他字段。(例如，更改一个日期，另一个日期也会随之更改)

让我们看看这是怎么回事！

## 请分享你的设置！我很想听听

**喜欢这个帖子？在我的博客上查看[原文，并在](https://antjanus.com/blog/thoughts-and-opinions/why-homogenous-dev-setups-arent-the-best-idea/)[推特](https://twitter.com/antjanus)T5 上关注我**
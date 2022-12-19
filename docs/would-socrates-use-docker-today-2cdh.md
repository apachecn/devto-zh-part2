# 苏格拉底今天会用 Docker 吗？

> 原文：<https://dev.to/nickjj/would-socrates-use-docker-today-2cdh>

**本文最初发布于 2017 年 11 月 7 日:[https://nickjanetakis . com/blog/would-Socrates-use-docker-today](https://nickjanetakis.com/blog/would-socrates-use-docker-today)T3】**

* * *

记得苏格拉底吗？他是 2500 年前非常聪明的希腊人。他最著名的学生是柏拉图，他负责奠定现代哲学和科学的基础。

苏格拉底留下的教导之一是一个叫做**苏格拉底提问**的概念。这是一种系统的方法，通过提问来非常详细地探索一个主题。

什么是苏格拉底式提问(引自[维基百科](https://en.wikipedia.org/wiki/Socratic_questioning))？

> 苏格拉底式提问是一种训练有素的提问，可用于多方向、多目的地进行思考，包括:探索复杂的想法、获得事物的真相、揭示问题、揭示假设、分析概念、区分已知和未知、追踪思维的逻辑含义或控制讨论。

事实证明，苏格拉底给了我们一个可以重复分析话题的方法。我们可以用这个做任何事。我们可以用它来做出重大的人生决定，挑选今晚的晚餐，或者找出哪些技术值得学习。

是的，这意味着 2500 年前发明的东西可以应用于我们今天面临的问题。顺便说一句，这就是为什么我试图在我的所有课程中同时教授“为什么”和“如何”的原因，因为理解这两者可以让你从复制/粘贴代码到能够解决你道路上的任何问题。

在本文中，我们将使用苏格拉底式提问策略来探究 Docker。

## 我们需要问什么问题？

如果我们回到维基，有一个部分列出了 6 种类型的问题:

*   理清思路
*   挑战你的假设
*   探究原因和证据
*   不同的观点和视角
*   含义和后果
*   质疑被问到的问题

这 6 类问题中的每一类都有许多子问题，可以用来探究任何主题。在列出它们之后，我们将看到如何将它们应用到 Docker 中。

这些子问题很多都是由[changingminds.org](http://changingminds.org/techniques/questioning/socratic_questions.htm)修改而来。这不是一个确定的列表，因为不存在确定的列表，但这是一个好的开始。

#### 理清思路

多想想你到底在问什么或在想什么。证明你声称的任何概念。

*   的本质是什么...？
*   你为什么这么说？
*   这到底是什么意思？
*   这和我们一直在谈论的有什么关系？
*   你能举个例子吗？
*   请你再说一遍好吗？

#### 挑战你的假设

探究你的假设，思考那些支持你论点的毋庸置疑的信念。

*   我们还能假设什么？
*   你是如何选择这些假设的？
*   你如何证实或反驳这个假设？
*   如果会发生什么...？

#### 探查原因和证据

深入你的推理，而不是假设它是已知的。

*   为什么会这样？
*   你怎么知道的？
*   如何反驳它？
*   我怎么能确定你在说什么？
*   有什么证据支持你的说法？
*   你的论点有什么根据？
*   你有证据支持你的断言吗？
*   这是相信这一点的好证据吗？

#### 另类的观点和视角

大多数论点都是从特定的立场出发的。所以进攻阵地。

*   为什么是...必要吗？
*   谁从中受益？
*   有什么区别...和...？
*   为什么它比...？
*   的优点和缺点是什么...？
*   ……怎么样...和...相似？

#### 含义和后果

暗示和结果是否有意义，是否可取？

*   怎么会...影响...？
*   如果发生了这种情况，结果还会发生什么？为什么？
*   那是必然发生的还是仅仅可能发生的？
*   怎么会...符合我们之前所学的吗？

#### 质疑被问的问题

*挑战并拆解问题。*

*   我们到底能不能把这个问题分解一下？
*   问题清楚了吗？我们明白了吗？
*   这个问题容易回答还是难回答？为什么？
*   为什么这个问题很重要？

## 对 Docker 应用苏格拉底式提问

既然我们有一系列问题要问，我们要做的就是回答它们。我不会回答每一个问题，但我会回答每个类别中的几个问题，这些问题普遍适用于 Docker 和技术选择。

这个练习的美妙之处在于，往往没有一个正确的答案。我很乐意在下面的评论中看到你对任何问题的回答。此外，如果您认为合适，请随意回答或询问其他问题！

#### 理清思路

多想想你到底在问什么或在想什么。证明你声称的任何概念。

*   **Docker 的本质是什么？Docker 提供了一种更好的方法来构建和发布你的应用程序。**
*   **这到底是什么意思？将应用程序的依赖项安装在不同的系统上可能是一场噩梦。Docker 允许你将你的依赖项构建到一个叫做 Docker 镜像的东西中，然后以同样的方式在 Windows、MacOS 或 Linux 上运行它。**

#### 挑战你的假设

探究你的假设，思考那些支持你论点的毋庸置疑的信念。

*   你如何证实或反驳这个假设？你可以通过用 Docker 构建你的应用程序，然后在 Windows、MacOS 或 Linux 上运行它来验证它的工作。您将看到它的工作原理是一样的，无需处理特定于操作系统的安装步骤。
*   **如果不使用 Docker 会怎么样？**您必须使用 rvm、nvm 和 virtualenv 等工具来隔离不同项目和语言版本的依赖关系。您还需要安装特定的操作系统级依赖项，这些依赖项会根据您使用的操作系统而变化。

#### 探查原因和证据

深入你的推理，而不是假设它是已知的。

*   有什么证据支持你的说法？如果您是一名 web 开发人员，您至少会在某个时候遇到设置开发环境的问题，并且会碰到这些问题。
*   你有证据支持你的说法吗？是的。试试看。也可以在谷歌上找到如何获得 Rails、Flask、Node 等。在开发和生产中运行的应用程序。你会发现这是许多人经常遇到的问题。
*   你的论点有什么根据？就我个人而言，20 年来我一直在以这样或那样的方式构建和部署 web 应用程序。在此期间，我开发和部署了 100 多个使用各种技术堆栈的 web 应用程序。

#### 另类的观点和视角

大多数论点都是从特定的立场出发的。所以进攻阵地。

*   Docker 给谁带来了好处？开发者可以更轻松地设置他们的应用堆栈。测试和 QA 团队可以快速启动应用程序，而运营团队可以跨环境移动完全构建的应用程序，这就消除了“它很适合我！”问题。
*   **为什么 Docker 比虚拟机更适合应用开发？**虚拟机会占用大量磁盘空间，浪费其他资源，并且需要很长时间才能加载。Docker 可以智能地利用磁盘空间，没有运行时性能问题，启动时间只有几毫秒。
*   **Docker 的优缺点是什么？**
    Docker 允许你轻松地使你的应用程序可移植，并鼓励尝试新的语言和工具，因为让它们以一致的方式运行是如此容易。

    Docker 的一个主要弱点是，从概念上来说，它很难在精神上“点击”，但是一旦点击了，你就会想“没有这个我怎么活？”。

#### 含义和后果

暗示和结果是否有意义，是否可取？

*   Docker 如何影响日常的 web 应用程序开发？
    你可以花更少的时间安装工具和依赖项，这样你就可以专注于开发优秀的应用程序。

    这既适用于编程语言运行时，也适用于外部服务，如 PostgreSQL、MySQL、Redis、Elasticsearch 或您的应用程序所依赖的任何其他服务。你可以用 Docker 运行它们。

*   那是必然发生的还是可能发生的？
    这种事总会发生。您可以将 Docker 用于解释语言和编译语言，并获得相同的回报。不管你用 Ruby on Rails，Flask，NodeJS，PHP，Golang，。网或其他任何东西。他们都和 Docker 一起工作。

#### 质疑被问的问题

*挑战并拆解问题。*

这个题型和其他的有点不一样。我们应该回答上述任何一个问题，并在提问的同时继续分解它们。

比如我们来操作一下**如果不使用 Docker 会怎么样？**

我们质疑这个问题的一种方式是:

*   我们能彻底分解这个问题吗？是的。不清楚我们在和谁说话。我们可以作为开发人员、运营经理、系统管理员、测试人员或 it 团队来回答这个问题，从而进一步探索这个问题。所有这些都有自己的问题，可以通过使用 Docker 来解决。

## 把东西包起来

如你所见，苏格拉底式提问非常有力。这几乎就像是列出一个利弊清单，只不过它更加系统化和结构化。这可以让你对任何话题有更深入的理解。

对于 Docker，我们仅仅触及了皮毛。如果我花一整天写这篇文章，它很容易变成 15000 字而不是 1500 字！

为了回答这篇文章的标题，即“Socrate 今天会使用 Docker 吗？”。我想他会的。当然这是我的观点，但是通过探索这些问题，我们已经确定使用 Docker 有明显的好处，苏格拉底是一个非常有逻辑的人。如果他今天还活着，没有理由认为他不会使用它。

顺便说一句，如果你认为 Docker 非常适合你，并且你确实想学习它，那么看看我的高级视频课程，它是[深入 Docker](https://diveintodocker.com/?utm_source=nj&utm_medium=devto&utm_campaign=socrates) 。它充满了大量的实际例子，在课程结束时，你将会在自己的项目中轻松自如地使用 Docker。
# 如何熟悉新的代码库

> 原文：<https://dev.to/perigk/how-to-get-familiar-with-a-new-codebase-i9f>

我们大多数人经常需要熟悉一个新的代码库。你可能是一个渴望为另一个项目做贡献的开源男孩/女孩，或者你刚开始一份新工作，你想熟悉这个将成为你未来几个月/几年生活中重要部分的平台…或者只是为了好玩，因为现在谁还看喜剧呢？

[![](../Images/d6df1fe7a41fadf5a78b36c4808c74ee.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--t5Fs4RXE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://cdn-images-1.medium.com/max/311/1%2AJs4O-RaZbAfFa-UIw_1LJw.jpeg)

在这个美丽的星球上，熟悉新的代码库是每个软件工程师都应该掌握的基本技能。

这些年来，相当多的人分享了他们的技术。但我相信，在掌握一项技能时，重复和协作是绝对必要的。

下面的方法着重于自己解决问题，而不是像你公司的架构师那样“依赖”他人的指导。

### RTFM 第一

首先，阅读任何可能与软件相关的文档。这可能是为项目构建的 wiki 页面，或者是从代码注释(如 doxy 或 Javadoc)构建的文档。

如果软件太大，那么你可能更喜欢专注于特定的领域。例如，如果您想熟悉整个脸书平台，您可以从了解新闻提要是如何填充的或者数据在数据库层中是如何构造的开始。用作需求参考的流程图、类图等总是很方便。

### 建造它，破坏它，摇动它(没有双关语[野人花园](https://www.youtube.com/watch?v=tJY6xGm_6f0))

在你获得了一些关于你正在研究的系统的基本知识之后，自然的趋势是去构建它。如果它不能被建造，也许它不值得阅读。

但是，如果出于某种原因你不在乎，理解构建是如何完成的(构建过程)对于你的最终目标是至关重要的。了解构建过程非常重要，因为您会了解依赖关系以及构建的代码是如何部署的。知道了依赖意味着什么，你就知道是什么破坏了你的系统。

在您构建它之后，开始像最终用户一样使用它，但不要只是沿着快乐的道路走。试着打破界面，看看系统的反应。

同时，观察产生的日志。这可能会揭示过程中的一些顺序，理想情况下，它会为您指出一个开始查看代码的入口点。

例如，如果您想检查系统的登录过程，就像用户一样登录。但是也许可以试着看看它对一些“形式攻击”的反应，比如 SQL 注入、T2 和 XSS。

如果日志暗示处理程序 handle_user_login 作为交互的一部分被调用，这完全是开始阅读逻辑的一个好的切入点。

### 读取自动化测试

当我说自动化测试时，我不仅仅指单元测试，还包括其他类型的测试，比如行为测试。)。这里有几个原因:

*   如果测试写得正确，就流程而言，它很好地展示了应用程序的预期工作方式。例如:

> 为了让用户登录，我必须使用测试中模拟的那 5 个功能，所以让我们更深入地检查一下。

*   单元测试是文档的重要来源。如果您阅读了模拟登录成功的单元测试，您就有了一个所涉及的函数及其返回值的很好的例子。函数 create_hashed_password 返回什么？它是布尔值还是散列本身？你现在可以验证。
*   行为测试是一种活的需求捕获机制。如果你不熟悉行为测试的概念，[这篇](http://docs.behat.org/en/v2.5/guides/1.gherkin.html)是一篇很好的文章，可以快速而准确地掌握。

### 开始阅读和画东西

现在你知道从哪里开始，开始阅读相关的代码。在我们到目前为止讨论的例子中，尝试理解登录处理程序是如何解析请求的。如何将解析后的密码转换为哈希版本，以及如何将其与我们存储在数据库中的密码进行比较。

不要害怕深入研究，更好地理解底层实现。但是，确保你约束自己，知道什么时候停止。否则，您可能最终会计划如何将数据刷新到数据库的速度提高 2 皮秒(当然，除非这是您的最终目标)。

试着去理解，为什么开发者以某种方式实现了一个特定的逻辑，你会怎么做。开始绘制逻辑图，这将有助于您可视化流程。

记笔记也是非常可取的。特别是，如果是内联注释，这将有助于以后重新访问代码，这次不会那么痛苦。在这种情况下，我倾向于用我的首字母作为前缀，以便以后过滤。

而验证自己理解的最好方法是什么？修改代码并编写单元测试。如果您添加的代码被调用，那么您肯定是在正确的轨道上。单元测试也是如此。如果你对你所研究的特性的逻辑没有一个很好的理解，你就不能写重要的测试。

### 详细追溯整个过程

现在你知道了，你关注的是正确的代码片段，你可以进一步深入到更多的细节。一个好的方法是在调用的代码中添加断点。也许可以启动调试器，开始验证变量和值的情况。

有没有在不同的地方初始化的，和你期望的不一样？它们有正确的格式吗，还是后来被[强迫](https://dev.to/promhize/what-you-need-to-know-about-javascripts-implicit-coercion-e23)？这个名字丑陋模糊的变量应该做什么？

在被检查的处理程序之前调用的函数做了什么准备？每个电话都有哪些假设，我们如何验证这些假设？

### 冲洗并重复

现在，您已经很好地理解了某一部分功能的情况，您可以选择另一部分。学习永无止境，永远令人兴奋。

### (可选)尝试添加新功能或解决 bug

这主要适用于开源项目，但对于“普通”企业软件并不禁止。一旦你对你正在检查的软件(或者至少是你最关注的领域)有了信心，试着增加一些功能，不管这是一个 bug 修复还是一个小的新特性。

这肯定会增加你对系统的信心，并且总是会给现有系统增加新的代码。

### 书籍阅读

*   [有效地使用遗留代码](https://www.amazon.co.uk/gp/product/0131177052/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=0131177052&linkCode=as2&tag=bitperi-21&linkId=98aa847bab0a8691243724c15d567a9a)
*   [代码读取](https://www.amazon.co.uk/gp/product/0201799405/ref=as_li_tl?ie=UTF8&camp=1634&creative=6738&creativeASIN=0201799405&linkCode=as2&tag=bitperi-21&linkId=4ae3be10ab8bd529e84cf6b41567b5fa)

感谢你看到这篇文章的结尾。如果您同意/不同意上面的任何步骤，请让我知道，正如简介中所暗示的，请随意添加您自己的方法。在那方面，你有什么好书推荐吗？

下面是我熟悉新代码库通常遵循的步骤的总结:

*   首先，阅读可用的文档
*   构建软件并像最终用户一样使用它
*   阅读自动化测试，开始第一次潜水
*   阅读实际的业务逻辑，并根据你的理解制作图表
*   详细追踪每个切片的全过程
*   一旦有了信心，就转向另一部分功能
*   给系统增加一些价值，通过修复一个错误或者增加一个新的小特性
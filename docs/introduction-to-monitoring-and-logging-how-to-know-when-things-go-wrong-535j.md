# 监控和日志记录简介:如何知道什么时候出错

> 原文：<https://dev.to/kylegalbraith/introduction-to-monitoring-and-logging-how-to-know-when-things-go-wrong-535j>

软件开发的现实是，事情总是会出问题。无论是行业还是应用，都难免在某个时间点出现断裂。

> 每件事都会失败。 *-沃纳·威格尔(亚马逊首席技术官)*

这个失败可能是因为代码中的逻辑错误。这可能是因为运行我们服务的底层基础设施出现了故障。或者我们的用户正在以一种你没有想到的方式使用系统。

失败的可能性是无穷无尽的。

但是我们作为开发者不应该因此而气馁。事实上，我们应该接受这一点，并促使自己认识到失败是会发生的。为什么？因为只有通过失败，我们才能使我们的应用程序更有弹性。

这就引出了一个问题，我们如何知道什么时候事情会失败？或者更好的是，我们如何知道事情何时开始失败？这里有一个重要的区别。

知道事情**已经**出了问题，就是**反应**。然而，知道事情**何时会变得**糟糕是**主动**。

### 收集故障信息

让我们从不知道开始，至少知道并应对失败。

知道事情何时出错的关键是我们的应用程序内部对与错的定义。我们举个例子。

这里我们有一个调用外部服务的 C#函数。对外部服务的调用包装在 try/catch 块中。

```
public void CallExternal()
{
    try
    {
        _externalService.MakeCall();
    }
    catch(Exception e)
    {
        //what does this mean?
    }
} 
```

Enter fullscreen mode Exit fullscreen mode

要知道我们的应用程序中什么时候出错了，第一步是**定义错误的**。看看上面的示例代码，我们可以问自己几个问题。

1.  如果我们在 catch 块中结束，这对这个特定的函数意味着什么？
2.  这个异常如何影响更大的系统？
3.  这个例外对我们的最终用户有什么影响？

这只是三个问题，但我想你能明白我想表达的意思。捕捉异常很好，但是我们必须知道这在系统的大环境中意味着什么。只有这样，我们才能知道什么时候真正的失败发生了。

这就把我们带到了知道什么时候出错的第一步，记录。为了知道我们的应用程序内部出了什么问题，我们需要记录应用程序内部的异常。

在确定这里的异常是一个错误之后，我们现在可以向我们的`catch`块引入日志记录。

```
public void CallExternal()
{
    try
    {
        _externalService.MakeCall();
    }
    catch(Exception e)
    {
        _log.Error("Failed to call external service", e);
    }
} 
```

Enter fullscreen mode Exit fullscreen mode

现在我们为自己记录信息，这样我们就可以知道我们的应用程序代码内部出了什么问题。这是关键，因为当故障发生时，我们需要知道**什么**出错了。伐木帮助我们到达那里。

我说*有助于*,因为有好的日志记录、一般的日志记录和坏的日志记录。在这一点上，我们有平庸的日志记录。我们知道发生了故障，所以我们记录了一条消息并包含了异常。但是那些木头去哪里了？或者换个说法，我们的日志记录是怎么实现的？

这就是好的伐木方法的用武之地。根据我的经验，良好的日志记录不仅仅是代码内部良好的日志记录实践，而是使这些日志在外部可见的可靠实践。

例如，如果我们的应用程序运行在 AWS EC2 实例上，而我们只是记录到磁盘上的一个文件，那么这些日志有多大用处呢？当然，它们比没有日志要好，但是我们仍然必须登录到机器上，下载文件并检查消息。

为了达到下一个级别，我们应该让这些日志对外可见。这可以通过将原木从机器上旋转下来并放入 S3 桶中来完成。也许我们可以改变我们的日志实现，直接写入 Kinesis Firehose，将我们的记录放入 Elasticsearch。或者，如果我们有钱，我们可以使用像 Sumo Logic 或 Data Dog 这样的提供商，将我们的日志转移到他们的系统中。

这里的要点是，为了让我们知道什么时候事情出错了，我们需要定义错误，然后在那些失败发生时记录信息。

这里需要注意的重要一点是，我们在应用程序内部使用 catch 块来定义错误的。这意味着我们的业务逻辑代码必须在遇到意想不到的事情时抛出异常。

这又回到了合理的日志记录实践。团队内部必须有一个日志记录的惯例，否则我们最终会得到缺少信息的稀疏日志。

我们现在处于被动状态。如果用户遇到问题，或者如果我们有一个基本的警报，我们可以对应用程序中发生的错误做出响应。

### 从被动转向主动

日志是伟大的，任何生产系统都应该拥有它。我们记录的消息让我们深入了解系统的行为和有关故障的信息。

在这一点上，我们处于被动的环境中。如果用户告诉我们发生了意想不到的事情，我们可以分析我们的日志来确定哪里出错了。

我们可以做得更好。事实上，我们总是想努力在用户知道之前知道事情何时出错。

这就是监控的用武之地。

这是一个广泛的话题，涵盖了整个系统。那么，我们应该监控哪些事情呢？

*   错误率。
*   我们系统的性能。
*   我们基础设施的健康状况。

这是三个非常宽泛的类别，所以让我们更详细地了解每一个类别。

#### 监控错误率

错误率是了解我们系统整体健康状况的一个关键指标。从骨料和细颗粒的角度来考虑这些是有用的。

后者允许我们利用现有的良好的日志记录实践。假设我们的系统中有两个函数，它们在错误发生时记录错误的细节。此外，我们通过将日志发送到第三方服务或直接记录到 AWS CloudWatch 日志，使日志对外部可见。

考虑到这两个先决条件，我们现在可以监控这两个函数的错误率。通过利用我们的日志记录，我们可以创建细粒度的监控策略，让我们知道某个特定的功能是否按预期工作。我们甚至可以进一步扩展我们的日志记录，以包括性能指标，这将允许我们知道生产中给定功能的性能。

在我们的系统中监控功能是一个细粒度的策略，但是监控整个系统的错误率也很重要。这使我们能够看到系统的总体健康状况。

这很重要，因为有了一个集合指标，我们就有可能发现系统中的问题。例如，如果我们的总错误率从 0 错误/秒上升到 1，000 错误/秒，我们就知道有问题了，可以开始深入细致的监控来确定原因。

细粒度监控和骨料监控确实是齐头并进的。事实上，我们甚至可以使用我们的细粒度监控来生成允许我们看到整个系统的错误率的集合。

#### 我们系统的性能

错误率是非常容易理解的，要么功能有效，要么无效。响应时间和性能并不明确，但对于成为一个积极主动而非被动的团队来说，它们同样重要。

测量和监控我们系统的性能使我们能够跟踪正在退化的系统的指标。与错误相比，绩效有更多的灰色区域。这是因为我们需要长时间地监控它，以便为一个健康的系统建立基线。

然而，一旦建立了基线，我们就可以监控我们的度量标准，在它们对我们的用户来说成为失败之前检测到降级。本质上，我们希望跟踪系统的性能，以便我们可以主动检测何时接近故障状态。

通过随着时间的推移监控系统的性能，我们可以将该信息与错误率结合起来，以了解错误是否会降低性能，或者性能问题是否会引入错误。两者都允许我们主动监控何时出现问题。

#### 我们基础设施的健康

像 AWS、Azure 和谷歌云这样的云提供商的现实是，有一个我们无法控制的失败宇宙。通过利用云提供商，我们可以将计算资源、网络和存储卸载给其他人。

这太棒了。它让我们能够专注于重要的事情，比如为用户构建一流的应用程序。

但是，我们必须认识到，这些服务也可能失败，当它们失败时，我们需要知道它。因此，我们需要持续监控基础架构的整体运行状况。

如果我们使用上面提到的三个云提供商之一，这里有一些我们可以监控的东西。

*   总体实例运行状况
*   负载平衡器运行状况
*   自动缩放失败
*   自动扩展和实例级 CPU 利用率
*   数据库内存、CPU、存储空间

这些只是值得监控的几件事。我们选择在基础设施级别监控什么将取决于我们的具体应用。例如，如果我的应用程序完全是无服务器的，我就不会监控负载平衡器或自动伸缩，因为它们不存在。

这里要记住的关键一点是，我们基础架构级别的故障通常是最严重的，因为它可能会导致整个系统瘫痪。因此，当失败确实发生时，我们需要了解它。

### 拉响火警警报

到目前为止，我们已经讨论了使用日志记录在细粒度级别上深入了解我们系统的行为。我们在函数级和聚合级监控错误和性能。我们还谈到了监控基础设施的整体健康状况。

这很好，我们知道了日志和监控的基本知识。但是这些只是让我们收集信息的工具，我们仍然需要知道**什么时候**出了问题。

当大楼发生火灾时，我们通常会拉响火警警报，让其他人都知道。我们提醒其他人，有一个问题需要立即关注。

通过记录关于我们系统的信息并监控组成系统的各个部分，我们可以使用这些信息在出现问题时提醒我们。这种警报可能是以下一种或多种情况。

*   向团队/支持人员发送短信。
*   向团队松弛频道发布消息。
*   向团队电子邮件列表发送电子邮件。
*   在共享工作区发出警报。

记录和监控我们的系统的目的是为了让我们在出现问题或即将出现问题时采取行动。警报是让我们采取行动的触发器。

我们可以从故障警报开始，因为故障已经发生，我们需要对其做出响应。也许这个失败来自我们的细粒度日志，或者我们的错误率以一种我们从未见过的方式激增。这可以让我们追踪导致故障的原因并解决问题。

从被动转向主动，我们可以开始实施主动警报。这与性能的主题非常相关。如果我们知道当我们的实例达到 95%的 CPU 利用率时，系统开始出现问题，那么当我们超过 85-90%时，我们可以提醒自己。允许我们了解系统的当前状态，并在达到故障条件之前采取措施。

### 结论

现实是大多数软件应用程序都存在故障。这些失败可能是由从糟糕的代码到基础设施等多种原因造成的。我们有责任知道什么时候出了问题。

日志记录是一种工具，它允许我们收集关于我们系统的信息。我们可以记录我们没有预料到的错误。我们还可以详细记录性能信息。然后，我们可以让这些日志在外部可见，这样我们就可以在不登录机器的情况下消化这些信息。

监控是一个附带的工具，允许我们查看系统的健康状况和性能。这种监控让我们知道我们是否需要研究日志中的问题，或者我们的基础架构是否遇到了意外问题。

警报是我们让自己对生产系统的健康负责的方式。只有当我们实际使用它们来响应一个动作时，日志记录和监视才有用。通过通知我们自己一个问题，我们让自己对这样一个事实负责，当一个问题出现时，我们需要解决它。

### 您是否渴望了解更多关于亚马逊网络服务的信息？

如果你想开始你的 AWS 之旅，但却不知道从哪里开始，可以考虑查看我的课程。我们专注于在 AWS 上托管、保护和部署静态网站。让我们在使用时能够了解超过 6 种不同的 AWS 服务。在你掌握了基础知识之后，我们可以进入**的两个额外章节**来讨论更高级的主题，比如基础设施代码和持续部署。
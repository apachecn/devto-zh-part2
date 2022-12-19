# 请停止使用 Ruby

> 原文：<https://dev.to/jimsy/please-stop-using-ruby-4lf1>

我知道你在想什么，但我想先说我爱露比。在对编程失去兴趣多年后，Ruby 是让我再次对编程感兴趣的语言。Ruby 振兴了我的职业生涯，让我成长为今天的高级软件工程师。Ruby 是一种可爱的语言。我只想你停止使用它。

对我来说，Ruby 是在 2008 年出现的，当时我在当地一个计算机科学部门担任系统管理员。我以前用很多语言编写过代码，甚至喜欢其中的一些，但是我从来没有像开始使用 Ruby 时那样感觉完全高效或与语言合拍。我和另一个团队成员一起构建了一个系统，使用 Rails、 [PXELINUX](https://www.syslinux.org/wiki/index.php?title=PXELINUX) 和 BitTorrent 的组合来重新映像实验室计算机。这是真正疯狂的科学。它也确实工作得很好，但这是另一天的故事。

在第一次接触 Ruby 并最终成为一名专业 Ruby 爱好者之后，我坚持使用 Ruby 的原因有很多。以下是我继续前进的原因，我认为你也应该继续前进。

## Rails——工作的最佳工具

如果你想在 2008 年开发 web 应用程序，那么 Rails 就是一个不错的选择。当然还有其他的选择，但是没有其他的选择是主流的，有合理的人才库并且经济实惠。

Rails 推动了后 GFC 时代的创业经济。不仅仅是因为潮人，还因为当你的潮人首席执行官决定将你的狗粮订阅网站转变为有机大麻跑鞋电子商务网站时，这是当时唯一一个允许你如此快速地高效工作并轻松调整应用程序的框架。

当时“工作”是一个相当受限的问题集:从数据库中取出一些东西，把它放在括号中，然后提供给用户。然后获取一些用户输入，并将其放回数据库。

如今，web 应用程序的领域已经扩展到包括 websockets、单页应用程序、拥有自己的查询语言的 API、web 汇编和一系列被称为“云”的技术。今天的 Web 应用程序的外观和行为与 2008 年的完全不同——除非你看看 Rails 应用程序。Rails 应用程序仍然在数据库和括号之间来回移动数据——只是现在括号的种类更多了。

## 语义——只能有运行

Ruby 的 DNA 来自于 Perl 和 T2 small talk 的混合体。像 Smalltalk 一样，Ruby 也有一个动态类型的经典面向对象范例。

Ruby 是一种脚本语言，这意味着 Ruby 解释器读入源代码，解析它，并立即开始评估它。没有正式编译步骤。运行时代码定义(并重新定义)常量、类、方法和其他一切。运行时代码可以编写更多的运行时代码，或者修改或删除现有的运行时代码。在某些情况下，同一个类可以有不同的行为，这取决于你所在的词法范围。Ruby 的语义非常灵活，难怪 Rails 会告诉每个人他们的代码必须放入三个文件夹中的一个。

在用 Ruby 设计系统时，你会听到很多关于[鸭类型](https://en.wikipedia.org/wiki/Duck_typing)的说法——只要对象响应你需要的方法，你就不需要关心对象的类型。这是一种不必事先定义协议的方式，这是有意义的，因为没有“事先”，只有运行时。在常规情况下，它工作得很好，因为大多数 Ruby 开发者都知道，如果你实现了`each`，那么你就可以成为一个可枚举的。

这在实践中意味着动态类型会导致微妙的错误，因为错误的对象在错误的时间出现在错误的地方。最常见的就是这种臭名昭著的`NoMethodError on NilClass`。这意味着你试图调用一个在`nil`上不存在的方法，但它真正的意思是在堆栈中你下面的某个地方，一个方法返回了`nil`，而不是你期望的东西。它没有告诉你你的 bug 在哪里，只是告诉你它的影响在哪里是系统最终无法忍受的。

因为 Ruby 的语义拒绝几乎任何类型的静态分析，而另一种语言的用户可以添加类型约束或至少模式匹配来避免这种情况，所以 Ruby 程序员只剩下一个选择:编写大量的单元测试，以正式确定允许哪些数据流入和流出方法和对象，以及当输入错误时它不会爆炸。

duck 类型化的另一个副作用是，在调用协作对象上的方法之前，通常会以`object && object.method`的形式进行反向类型检查，以验证协作对象至少是真实的。这是如此普遍，以至于 Ruby 2.3 增加了`&.`安全导航操作符，将这个设计问题变成了一种美德。

## 性能——只能有一个

首先让我们把这个拿出来。[红宝石是*慢*T3】。传统观点认为 Ruby 已经“足够快”了，你总是可以在一个问题上投入更多的硬件。这在一定程度上是正确的，但是现在大多数机器都是多核的...](https://github.com/kostya/benchmarks)

> 我不认为我自己是线程的人，所以我不认为我能对 Actor 库或线程库做出正确的决定。
> [马茨——红宝石的创造者](https://www.jstorimer.com/blogs/workingwithcode/7766069-matz-is-not-a-threading-guy)

...Ruby 也不擅长并发。MRI 有一个全局解释器锁，这意味着一次只能运行一条 YARV 指令。有很多地方可以解决这个问题——比如等待 IO 的休眠线程，但是基本上，如果你想一次做多件事，你需要运行多个解释器进程。

最后，Ruby 倾向于[使用大量的内存](https://www.sitepoint.com/ruby-uses-memory/)，并且不喜欢将内存归还给操作系统。有办法在一定程度上缓解这些问题，但大多数 ruby 爱好者并没有意识到这些问题，或者只是习惯了这种情况。

在过去的几年里，Ruby 核心团队投入了大量的工作，我将是第一个承认 Ruby 2.5 比过去快得多的人。许多人会认为这已经足够快了。我不会。

## 韧性——例外情况

如上所述，即使是多线程运行，Ruby 本质上也是运行一个没有内置容错原语的解释器，所以未处理的异常会导致整个 VM 瘫痪。社区在编写演员系统方面做出了传奇般的努力，但最终这些团队放弃了，转而使用语言，这些语言为他们提供了在产品中构建可靠性所需的工具(例如[赛璐珞](https://github.com/celluloid/celluloid/issues/779))。

## 工装-从 0X 到 DX

Ruby(尤其是 Rails)社区在帮助开发人员快速取得成果的良好工具方面处于领先地位。像 Rake、Bundler、RSpec 和 Rails 命令行这样的工具确实为开发人员的体验开辟了一条道路，但是其他语言已经在工具游戏中赶上甚至超过了 Ruby。Rust 的 [cargo](https://github.com/rust-lang/cargo) 、Elixir 的 [mix](https://elixir-lang.org/getting-started/mix-otp/introduction-to-mix.html) 和 Scala 的 [sbt](https://www.scala-sbt.org/) 都将这些工具组合到一个命令中，并进一步将它们直接紧密集成到语言中。不仅是语言提升了他们的工具游戏，客户端框架、DevOps 系统和云提供商也是如此。

## 包裹——通向无限和更远

Ruby 幸运地拥有大量的包(或者 gems ),这些包提供了你能想到的几乎任何种类的功能。没有其他语言[那么多，但我认为平均来说它们质量要高得多。需要开箱即用的身份认证系统吗？](https://www.npmjs.com/)[有一颗宝石代表那个](https://rubygems.org/gems/devise)。需要一个被夸大了的、在架构上有问题的状态机，奇怪地与你的数据库绑定在一起吗？这也是一块宝石。

在 Rubygems 之前，真的只有 CPAN，但没人需要被提醒。Ruby 的易于消费和集成的包的模型铺平了道路，并被许多其他语言采用，例如: [crates](https://crates.io/) 、 [hex](https://hex.pm/) 、 [CocoaPods](https://cocoapods.org/) 和 [elm/packages](https://package.elm-lang.org/) 。

## 那么 2018 年我该用 Ruby 做什么呢？

对我来说，`irb`仍然是我用来快速解决问题的工具，我仍然会编写一些小的 Ruby 脚本来协调一些一次性的工作，比如移动文件或者下载 API 响应。

当我们谈论 Ruby 时，很难忽略 Rails，所以我想问题是“2018 年我应该用 Rails 做什么”？如果你有一个符合以下标准的应用，那么我认为 Rails 仍然是你的最佳选择:

*   几乎完全是数据库驱动的，
*   在服务器上呈现页面或生成 JSON，
*   大部分可以由现有的宝石组装而成，
*   没有复杂的业务逻辑，
*   不需要很快，
*   不需要同时服务很多人，
*   永远不会改变。

尽管如此，我还是认为你有更好的选择。
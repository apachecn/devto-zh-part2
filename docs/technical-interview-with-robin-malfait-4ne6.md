# 罗宾·马尔费特的技术采访

> 原文：<https://dev.to/kyleparisi/technical-interview-with-robin-malfait-4ne6>

我今天尝试一些不同的东西。我曾经在 twitch 上直播过流媒体 web 开发。在那段时间里，我只吸引了几个观众。其中一个观众变成了永久的友谊。比利时的罗宾·马尔费特。罗宾的编程能力总是给我留下深刻的印象。这是一篇关于他编程经历的采访。

### 简单说说你是谁。

我是来自比利时的开发人员罗宾。我更喜欢 JavaScript 这种编程语言，目前是 React 的忠实粉丝。我也在一家名为 Skedify 的初创公司工作。

### 你是如何进入编程行业的？

我认为 JavaScript 对我来说有很多有趣的地方。首先，你不需要一个复杂的环境，你可以在你的浏览器中运行它，它就工作了。这是一个大问题，因为每个人都可以贡献和运行它，而不需要一个复杂的系统。也就是说，现在情况完全相反，因为所有的 JavaScript 都是编译/传输的。另一个有趣的事情是，JS 是唯一运行在你的浏览器中的“编程语言”(不做任何类似 Java 小程序的事情，...).我也喜欢 JavaScript 的灵活性，因为当我上 Java 课程时，你必须键入所有内容，虽然这很好，但我有时会觉得我在与编译器战斗，而不是专注于纯粹的领域逻辑。目前，我喜欢 JavaScript 正在进步的事实。它有很好的 API 和语法。例如 arrow 函数，async，await，它也变得非常快，这对每个人都有好处。

### 你对 react vs vuejs 有什么看法？

我更喜欢 React，我不能说很多关于 vue 的事情，因为我从来没有真正使用过它。但这让我想起了你必须学习这个特定 DSL 的 angular 1.0 天。我认为 Vue 非常适合快速原型开发，因为 React 更加冗长，而且你需要更多的代码来创建一个简单的计数器。但是现在有了 React Hooks RFC，我想我会继续使用 React，因为现在冗长的代码被大大简化了。

### 我记得你跟我说过你们公司的 lint 规则。我觉得他们很激烈。你能描述一下这些以及你对它们的感觉吗？

基本上，在 eslint 中有两种“规则”。你有让你成为更好/更快的开发者的规则，它们有点像编译器，例如“变量 x 没有被定义”或者“常量 x 被定义了两次”。除此之外，你还有代码风格偏好的林挺规则，这些规则给了你对拉请求无止境的挑剔。“请你在那里放一个空格，请你加一个分号”等等。因此，在我工作的地方，我们有一个相当大/密集的 eslint 文件，其中有一些荒谬的东西，例如，冒号周围应该有空格:`const position = { x : 1, y : 2 };`。我不喜欢这样的规则。但是，有一个很好的解决方案，有更漂亮的，基本上漂亮做的是格式化你的代码到一个通用的代码风格。这允许你忽略造型规则，让漂亮的人来处理它。自从我们引入了更漂亮的代码，我们再也没有代码风格的挑剔了。然而，这是事实，漂亮有时做的事情，团队不喜欢，但我们达成共识，我们让漂亮处理。所以现在我们从 eslint 中去掉了所有代码风格的东西，只使用“编译器”式的规则。完美地工作。

### 但是不是有“不允许 for/while 循环”之类的规则吗？

哦，是的，那是真的，那些还在那里。所以我们没有 for，没有 while 等等，所以我们被迫在命令式代码上写更多的函数式和声明式代码。所以“不 while”可以用递归代替，“不 for”可以用`array.forEach`或`array.map`类函数代替。它们有时看起来很难，但是因为我是这样写的，所以我对它们没有问题。哦，还有总有`/* eslint-disable-next-line */`😊。我必须承认，一开始那些规则是疯狂的，因为我总是写 for 循环和 while 循环。

### 那你现在感觉如何？

我已经习惯了。另外，我写了很多 react，所以无论如何你要写更多的声明性代码。比如`<ul>{items => items.map(item => <li key={item.id}>{item.text}</li>)}</ul>`。你不必先创建一个数组，用 for 循环遍历它，然后创建`<li>`元素并输出它们。我还认为，由于这些规则，代码可读性更好，也更容易掌握。除非你有奇怪的算法，你必须使用递归，这些让你很难思考。

### 您日常使用的工具中有哪些不太为人所知？

你知道阔卡吗？

### 没有。

你会喜欢这个的。所以对你的编辑来说，quokka 是一个很棒的工具。可以把它想象成 devtools 控制台。你可以写代码，它会被执行，但你甚至不需要保存一个文件，它会一直这么做:[https://quokkajs.com/](https://quokkajs.com/)。您可以在其中编写节点代码，它会为您运行它。我一直用它来制作小东西的原型。

[![quokkajs](../Images/ef3d0af47d55e8fe56765efc01467ee4.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--snU_Uri0--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/knvkcl928af75i9avbbd.png)

我喜欢的其他工具是`bat`，它是`cat`的替代工具，具有语法高亮、行号和对终端的 git 支持。https://github.com/sharkdp/bat

### 我很好奇，你用过调试器吗？

你谈论调试器很有趣，因为我很少使用调试器。我能很快理解代码，所以简单的日志就可以了。也有其他控制台工具可以帮助，例如 console.table，在一个漂亮的表中记录您的对象/数组。然而，我遇到的恼人的问题无法解决，或者至少不容易解决。例如，比赛条件。每次我试图在那里使用调试器时，问题都没有发生，因为调试器让你按顺序逐步通过它，即使事情是异步和“并行”的。也就是说，我们确实需要在工作中支持 ie10，所以我确实使用了调试器，因为控制台太差了，我不能检查对象等等。

### 一般是遵循 TDD 还是写测试？

我不严格遵循 TDD，但是我确实写测试，不然晚上睡不着。我的意思是，我一直在没有测试的代码库中，我害怕接触任何东西。

### 你对这些测试有什么看法？只有东西坏掉的时候？

不，我确实在编码时写测试，不仅仅是当东西坏了的时候。所以，我有多种方法，这取决于我那天的心情。所以，有时我会写一堆测试，这样我就可以玩某个函数的公共 API，这样我就可以玩*我想如何*使用那个函数/代码。其他时候，我在编写了一段代码之后编写测试来验证它是否真的可以工作。所以我确实写了测试，但是我没有遵循严格的红色- >绿色- >重构方法。

### 对于 web 开发的初学者，你会给他们什么样的建议？

哦，有很多东西要学，好吧，让我想想。首先，我认为有很多东西要学，有很多框架，所以不要试图一次学会所有的东西，这会让你很快陷入不愉快的状态。除此之外，找一些导师也是一个好主意，这样你就可以在现实生活中认识开发人员。也试着创建一些兼职项目，这样你就可以在工作中真正使用网络技术之前先玩玩。还要努力掌握好 JavaScript，因为如果你非常了解 JavaScript，那么像 React 和 Vue 这样的节点或前端框架就更容易掌握。

### 关于你是如何掌握 javascript 的，有什么建议吗？

我写了很多垃圾代码。就像我之前说的，我只是玩了很长时间，所以我没有看任何课程。不过我可以推荐韦斯博斯[https://javascript30.com/](https://javascript30.com/)(免费)和[http://es6.io/](http://es6.io/)(付费)的课程。我也在 Twitter 上关注了很多来自不同团队的开发者，比如 Chrome 团队，或者 React 团队。他们展示了很多代码片段和我每天学习方法。

### 哪里可以让别人更了解你？你有时也住在溪流里，对吗？

我计划在 twitch[https://twitch.tv/robinmalfait](https://twitch.tv/robinmalfait)上发布更多内容，你也可以在 Twitter[https://twitter.com/malfaitrobin](https://twitter.com/malfaitrobin)上找到我。
# 让我们再试一次！

> 原文：<https://dev.to/ashe/lets-try-this-again-3hk8>

如果有人真的在关注我，那么你可能已经注意到一些博客已经消失了。下面是我经营自己游戏工作室的一年的最新进展，以及我现在在做什么。请注意，这篇博客已经被重新利用，以展示现在和去年之间的一些差异，因为我不应该在这篇博客中使用旧工作室的资产。

## BestInSlot 工作室，怎么回事？

我的工作室 BestInSlot 并没有完全按照我的计划进行。由于我们分开了，原来的六个人中还剩下两个人。我要说的是，我生活中的个人事务给我带来了很大的压力，但我真的尽了最大努力让一切都保持在一起，让人们保持动力和生产力，直到我意识到这种心态并不是每个人都有的。在一次大学作业中，你被一个团队撞了进去，如果你想得到一个更好的分数，你必须努力争取。分数制度从来都不公平，所以当你完成大部分工作时，你所带的人仍然会达到相同的分数。然而，这一年是不同的——我们是一个由五名程序员和一名艺术家组成的团队，他们挑战自己做出一些东西。手头的任务不是你能在一周内完成的，所以如果有人没有尽自己的一份力，那么简单地为他们做不会有什么效果。

[![GitHub statistics showing commit activity on our first game](../Images/b2bf68f709d9b5d0ffbb8b1bcf343339.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--3xjdgkA0--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://res.cloudinary.com/aas-sh/image/upload/v1617291991/blog/2018/03/git_commit_graphs_af28w0.png)

从这个意义上说，这是我第一次领导一个团队，在这个团队中，我不能简单地微观管理每个人以获得结果。当我们开始出现问题时，我不得不尝试不同的方法来激励人们。随着时间的推移，我的压力越来越大，在我们的一次会面中，很明显，沟通的质量没有达到我想要的标准。GitHub 上的东西没有被阅读，人们的意见必须经过处理才能清楚。我们和大学的导师会面，进行一年的中期回顾。这是一场狗屎秀。导师们知道我很努力，所以当我对 GitHub analytics 透明时，谁在工作，谁不在工作就一目了然了。我可以自信地说，我尽了最大的努力做好自己的分内事，让自己更上一层楼，除了一个人之外，我不能对团队中的其他人说同样的话。最后，我决定把自己从等式中去掉，这样不仅对我自己有利，对所有人都有利。虽然他们一开始很生气，但我认为我的离开给了他们一个重新开始的理由，并有望从中受益。

我不能说我没有错——关于项目的规划，我犯了几个严重的错误。根据我们大学前一年的经历，我们讨厌 Trello，因为我们被迫使用 Trello+,这感觉不自然，而且超出了我们所用项目的范围。回顾过去，我现在确切地知道使用像 Trello 这样的项目管理工具是多么的重要，以便推进开发周期，并真正地得到一些东西。既然说到这个话题，我强烈建议你去看看 [Taiga.io](https://taiga.io) 。泰加刚刚宣布了一个新的定价方案，这可能会让那些现金短缺的人更感兴趣(请注意，现在是每人一份——如果你邀请某人参加你的项目，那么你必须付费。他们的支持者说，他们 ***正计划发布一项计划，你只为自己付费，其他人必须为自己的会员资格付费。***

[![Taiga.io](../Images/063e73433cea0b0d33b4e987a286ec22.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--p3uQPbyT--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://res.cloudinary.com/aas-sh/image/upload/v1617292161/blog/2018/03/taiga_screenshot_e9prnh.jpg)

反正我跑题了，去你妈的 [Taiga.io](https://taiga.io) 这么好！虽然人们*说*他们对特雷罗不感兴趣，但我现在意识到球队并不总是说出他们的想法。我真的应该更详细地考虑一下我们将如何计划我们的项目。我知道对所有事情进行投票会花很长时间，所以在一次会议上讨论完游戏后，我的得力助手和我一起通宵起草了一份 GDD。我们用颜色来区分我们讨论过的事情和我们认为很酷并希望人们思考的事情。在将它设置为只读后，我们让团队成员随意看看他们是怎么想的。然而，几个月过去了，结果是团队不喜欢事情的处理方式，并把他们的意见藏起来，直到事情升级。我没有意识到我非常喜欢做的游戏并不是其他人想要的。

我把角色委派给需要它们的人。我告诉艺术家，他们对艺术方向有完全的控制权，因为他们比我更清楚，他们可以用资金来寻找自由职业者或购买资产等。有了五个程序员，我发现我们可以快速地完成大量的样板代码，然后进入有趣的部分。我想让人们拥有他们想要的领域，并真正成为他们自己的——在我的领域(我与我的得力助手分享),我很快就有了类似关卡编辑器的东西，玩家可以在那里创建房间并将它们组装在一起，随着它们的移动改变墙壁、门和物体的位置和外观。我把它做成可修改的，序列化了所有的东西- *甚至是艺术*。我很自豪能在这么短的时间内学到这么多关于 [Unity](https://unity3d.com/) 的知识，即使我并没有像接触脚本系统一样接触编辑器。

我算错了。我用自己的时间工作，如果需要，我会请几天或几周的假，因为我完全相信自己能完成工作。我生活和呼吸着代码，今年我选择这样做，当这是我的愿望时，我为什么要偷懒呢——做一些我认为我做不到的事情。然而，这并没有被其他人理解。没有任何资金来支付我们自己，我们不得不投入时间的唯一原因就是我们自己的动力。我是一个有上进心的人，但后来发现并不是所有人都这样。人们把兼职工作放在工作室之前，英雄联盟接管了关键时刻。我正在谋杀我的睡眠时间表和这个工作室的空闲时间。当然，我喜欢它，但问题是我不得不离开，因为这些障碍是由人们根本不工作造成的。

## 让我们再试一次

总而言之，我与工作室分道扬镳，因为我为六个雄心勃勃的人审视了这个项目，而我因为认为在大学里做游戏的人会无偿地为一个个人项目努力工作而受到惩罚。我从这次经历中学到了很多，我一点也不后悔。据我所知，他们的工作室进展顺利，我知道我们正在制作的测试 Steam 的小游戏进展顺利。剩下的时间不多了，我写这篇博客是为了回到工作室去南方之前- *当然带着我的知识*。当我明年回到大学时，我会比以前更加努力地学习，因为我知道这两年是理所当然的。

我将再次写博客，因为它很有治疗作用，现在我没有了一个大团队的压力，我可以再次找到时间做有趣的事情。例如，我目前正在学习 Haskell，这是我现在最喜欢的语言。引用今天早些时候我自己的话，*我觉得我要成为素食主义者了，但是在编程世界里；我忍不住去尝试，却又试图说服人们去尝试*。如果你想学习它，你应该考虑购买 [HaskellBook](http://haskellbook.com/) 或者简单地尝试黑[学一个 Haskell 来获得一个巨大的好处](http://learnyouahaskell.com/)。它与[命令式编程](https://en.wikipedia.org/wiki/Imperative_programming)完全不同，即使你最后不使用它，也会让你受益。我目前正在通过游戏开发进一步提高我的 Haskell 技能，因为我非常了解 [SDL2](https://www.libsdl.org/index.php) 。我再次离开 Unity 纯粹是为了遇到和克服更多的挑战，就像我在测试 [SDL2](https://www.libsdl.org/index.php) 和 [SFML](https://www.sfml-dev.org/) (后者如下图)时一样。

[![A simple SFML game I made from scratch featuring Spine animation support](../Images/8412ce0074be42652790bb3e57027f9a.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--jJE6m0Ur--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://raw.githubusercontent.com/Ashe/Deus_Vult/master/img/preview.gif)

正如我所说的，我不后悔任何事情，但是这次经历让我对游戏开发的实际进展有了难以置信的了解。大学作业中的第一个(最高分)只是一个原型，从那一点开始，游戏中有很多工作要做，以便为发布做准备。有时候，这个打磨阶段实际上比游戏本身更费时间和精力——我们现在的游戏是在一个 48 小时的个人游戏中制作的，我是参与者。现在我们只是增加了关卡，UI 和生活质量的更新。 ***我讨厌它*** 。编程的乐趣对我来说就是挑战；来实现以前没有的东西。我已经完成了有趣的部分，设计师和艺术家可能会喜欢的东西我 ***厌恶*** 。

虽然我的愿望是拥有一个游戏工作室，在那里我可以大量充实游戏的机制和背景，但我现在知道，如果没有拿薪水的员工，我将很难生存。在此之后，我的观点发生了转变，现在我会更加珍惜在游戏团队中的时光，因为我知道了总的工作量。我可以向你保证，这场比赛之后，我不想再被非数学的工作缠住了！正是基于这一点，我得出结论，学习 Haskell 以尝试在游戏开发之外的领域就业，肯定是我今年的收获，以及管理一支我没有正确评估的团队的经验。

## 感谢阅读！
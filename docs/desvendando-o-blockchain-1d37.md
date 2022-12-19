# 区块链的德斯文丹多

> 原文：<https://dev.to/fguisso/desvendando-o-blockchain-1d37>

中本聪介绍对等电子货币系统概念的论文至今已近 10 年，你还不知道比特币是什么，更不用说 Blockchain 了。那我们走吧，因为我们还有时间进入浪尖！

[![In Blockchain we trust!](../Images/4bef687838ca45c91fc3bf94792bd2a3.png) ](https://res.cloudinary.com/practicaldev/image/fetch/s--0J4qPOdE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://cdn-images-1.medium.com/max/2000/0%2AJqgiftyvFtTFVAao.jpg) *我们信任的区块链！*

对于 5 岁的孩子来说，有一些文字来解释这个概念，但是在我们生活的这个时代，这些孩子天生就知道，所以不要在阅读这样的文字时感到气馁，你一定能看到这个概念，然后去更技术性的部分。下面是我一直使用的一个例子，我非常喜欢它:

### 苹果交换

我们坐在伊比利亚公园的一个长椅上。天气真好。我带了一个苹果给你。

[![](../Images/0e79baa510288eea723d6c4b36cc2b1a.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--kbWz8baK--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://cdn-images-1.medium.com/max/2000/0%2Ads2ohSBurU8x40Ss.jpg)

你现在有一个苹果，我有零。很简单，对吧？

我的苹果实际上是放在你手里的。你知道发生了什么。我在那里，你在那里--你碰了她。

我们不需要第三方帮助我们转账。我们之间不需要法官来确认苹果是从我传给你的。

现在苹果是你的了！我不能再送一个苹果了，因为我再也没有了。我再也控制不了她了。苹果从我手里拿走了。现在你完全控制了苹果。你可以把苹果交给朋友，如果你愿意，那么你的朋友可以交给他的朋友，等等。

现在，假设我有一个数字苹果。我把我的数码苹果给你。现在事情变得有趣了。

你怎么知道原来是我的数字苹果现在是你的了？想一想。这是一个有点复杂，对不对？你怎么知道我没有把这个苹果作为附件邮寄给我叔叔。或是我朋友约翰。还是我的月亮朋友？

也许我在电脑上复印了那苹果的几份。也许我把苹果放到网上下载给了一百万人下载。

如你所见，这种数字交流是一个问题。发送数字苹果似乎不等于发送物理苹果。

这里我们有一个大的计算问题叫做□或□

一个解决这个严重问题的办法是在数码图书中做交易记录。这样就有人跟踪我们的苹果我们就可以安心了，问题解决了！

我们这里还有两个问题:

1.  拥有数位书的人可以创造任意数量的苹果。

2.  这和我们在伊比利亚公园的日子不一样那时只有你和我。一个掌控着这本书的人就像在我们交易的中间放了一个法官。

但是我怎么能像平常那样和你交换数码苹果呢？

如果我把这本书给大家呢？而不是只和几个人在一起，他会在每个人的电脑上。所有曾经发生过的交易都会被记录在数字苹果里。

你骗不了我，我不能送我没有的苹果，因为那样我就不能和系统里的其他人同步了。这是一个很难打败的制度。尤其是当它变得太大的时候。

更重要的是，它不是由一个人控制的，所以我知道没有人可以决定给自己更多的数字苹果。系统规则已在启动时定义。

代码和规则是开放的，您还可以参与网络--更新书籍并确保完成所有工作。对于问题，你可以得到 25 个数字苹果作为回报。事实上，这是在系统中创建更多数字苹果的唯一方法。

## 加密与挖掘

好吧，到目前为止，我们已经了解了数据块链的概念，但这种著名的概念是从哪里来的，以及加密如何帮助系统使陌生人可以信任？

按照数字图书中苹果交换的路线，书中的每张图纸，我们称之为区块，就是其中包含了一些记录交换的地方。书中的每个区块都包含前一个区块的[杂凑](https://pt.wikipedia.org/wiki/Fun%C3%A7%C3%A3o_hash)(代表完整档案但大小特定的演算法结果)，除其他资讯外，建立区块链以计算新杂凑。

为了一个新的区块进入书里，需要做一个数学计算，尽管简单(“T0”开采手中的比特币，但要做起来需要时间，所以电脑可以做得快得多。

比特币网络每十分钟改变一次这个数学账户的数值让随机决定哪台电脑能做到先算。这些整天都在做这个账单的电脑，我们称之为& lt；和每一个采矿区块，它们都获得了回报，所以处理能力仍然值得。

现在，如果网络上的每个人都需要做这个计算，那么比特币可能不会增长那么多，这就是为什么块计算算法需要时间，但是验证计算要快一点。因此，在一些计算机找到块计算后，其他计算机只需验证此帐户。

让我们想象一下一个塑料艺术家，他需要用不同颜色的混合物为他的画创建一种颜色。他仍然只看到他脑海中想达到这种混合的颜色，所以他需要反复测试直到达到预期效果，就像计算新块的艺术一样。但是，当艺术家达到想要的颜色并应用他的作品后，当他需要这种新颜色时，他已经有了一个参考，他没有记下达到结果所需的颜色数量，但是有了参考，测试到相同颜色就容易得多了。因此，当我们已经计算出一个块时，由于结果必须是真的或假的，因此更容易进行验证。如果是假的，块不进链，还得有人计算块的实际值。如果是，网络上的其他计算机可以将块添加到您的链中。

## 从零到四

现在你已经了解了 Blockchain 的工作原理，我们将带来更多的新闻。虽然 Blockchain 是一个概念，我们有各种各样的变体，但我们使用版本来表示我们处于什么样的想法时代。

### 区块链 1.0

一切的开始，或者至少当事情发生并形成的时候，比特币。第一个用于加密的 blockchain 示例，一种交换和金融交易的记录形式。*上网钱的时间。*

### 区块链 2.0

给机器人打电话，Smart Contracts 的浪潮来了。智能合同，在 blockchain 中注册以便自动执行。在此字段中，ethereum block chain 是创建 Smart Contracts 的最常用方法之一。

### 区块链 3.0

到目前为止，Smart Contracts 是以编程语言编写的，在某个课程中学习编程的律师表现良好。其他人无法与这些新合同进行交互，这时 Dapps(分散式应用程序)应运而生，它只是一个使用 Smart Contracts 作为后端的系统，并且具有一个前端层，使普通用户能够与 blockchain 进行交互。

### 区块链 4.0

这是一个与另一个新概念的比赛，工业 4.0，在那里你使用 IoT 将工业机器连接到网络。将密码锁、Dapps 和 IoT 结合起来，我们进入了分块链的新阶段。
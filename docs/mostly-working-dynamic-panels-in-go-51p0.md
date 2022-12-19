# 主要在 Go 中工作动态面板

> 原文：<https://dev.to/progrium/mostly-working-dynamic-panels-in-go-51p0>

我一直在把 Dan 的类似 Photoshop 的 UI 原型移植到我的 web UI 堆栈中。我接触到了项目中最复杂的代码，也就是这些动态面板组。Dan 将这段代码分解到一个独立的项目中，这个项目比 Photoshop 原型要早一点。

这个项目有一堆简单的例子，我可以用来看看它一旦被移植就会工作。这花了很长时间。我主要是在不真正了解它是如何工作的情况下移植的。我明白了大概的意思，但是我必须更专注于弄清楚所涉及的类型以及组件的属性，因为这些都不是显式的。

移植到 Go 相当简单，我只是一点一点地理解发生了什么，然后做一个惯用的 Go 版本。通常这更具可读性，但我也认为 Dan 并没有花太多时间来清理这一部分。

最后，我写完了代码，并开始利用编译器错误来解决我对类型的解释中的任何不一致之处。我最终修补了 Vecty，因为它做出了一个可能不再相关的断言。最后，我可以让演示页面正确无误地呈现出来，但是它能正常工作吗？

算是吧。它有一点反应迟钝，显然数学在某个地方出错了。我很可能在实现算法时犯了一些错误。我在第一次传球时发现了一些错误，所以我确信还有更多。但是没有反应让我对使用 WASM 进行交互动画感到好奇，比如这个滑动交互。我知道打电话进出 WASM 比较慢，但是有那么糟糕吗？

我制作了一个单独的组件来测试拖放，并观察它在没有任何其他事情发生的情况下的执行情况。不可怕，但远不如原生 JavaScript 流畅。我看到火狐在加快 WASM 之间的通话速度方面有点领先，所以我在那里试了一下，看起来确实流畅了一些。

[![draggable experiment](../Images/9e50bb6f82e11563dc0c49d73067131c.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--JxLPB00N--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/9ht8mhnnzu0gogp186zt.gif)

两种浏览器最终都会快得多，目前这还可以忍受。这给了我它应该如何表现的基线，但显然还没有。但我觉得只是从这里开始调试。

显然还有更多工作要做，但这是一个有趣的练习，有助于填补我的堆栈的空白，并获得使用它构建真正组件的经验。有他们真的很酷。
[https://www.youtube.com/embed/wZeEaOeEvmk](https://www.youtube.com/embed/wZeEaOeEvmk)T2】
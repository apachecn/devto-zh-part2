# 你解决的最有趣的编码问题是什么？

> 原文：<https://dev.to/lpasqualis/what-is-the-most-fun-coding-problem-you-resolved-2ep>

在我的职业生涯中，我从编码中获得了很多乐趣。然而，有几个问题，我仍然深情地记得，解决起来特别有趣。它们不是我工作中最难的，也不是最重要的。然而，在当时，他们给了我一种巨大的满足感，这种满足感我至今仍记忆犹新。

这里有两个例子:

## 广告概率

早在 2000 年，我就在为一家托管公司开发在线广告系统。我有一个横幅列表，需要在网页呈现时随机显示。对于每个横幅，我都有一个与之相关的百分比。该百分比表示该特定横幅在系统中的网站上显示的概率。

我必须编写代码以正确的频率显示广告。该系统每天会收到数百万个请求(在当时是一个巨大的数字)，它必须具有很高的性能。我花了很大力气研究那个问题。我实现的解决方案简单而快速(最坏的情况是 O(log n))。这些年来，我针对不同的问题使用了不同的版本。

## 快速内存分配

第二个是在 2003 年，当时我试图优化一个运行在移动设备上的虚拟机。当时移动设备速度很慢。非常慢。虚拟机在特定的设备上表现不佳，我花了一些时间对它进行了分析。代码是用 C++写的，我意识到让事情变慢的是设备上的内存分配系统(并不令人震惊)。

每当用“new”创建一个对象时，分配程序都要花很长时间来完成它的工作。我决定创建自己的内存分配器，为我正在运行的特定应用程序进行高度优化，这碰巧创建了许多非常小的对象。结果是整体性能立即提升了 95%。

## 你呢？

还有很多其他的，我就讲到这里。你呢？在你的记忆中，有没有解决起来特别有趣的问题？它们是什么？

* * *

### 如果你喜欢这篇文章，请保持联系！

*   在 CoderHood 上找到我所有的帖子。不要忘记订阅邮件来接收新帖子的通知。
*   在 LinkedIn 上加入我的职业网络。
*   在推特上关注我。
*   加入我的脸书主页。
*   最后，请在 dev.to 上关注我！
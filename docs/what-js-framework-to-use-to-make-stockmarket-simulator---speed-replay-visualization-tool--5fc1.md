# 用什么 JS 框架制作股市模拟器-快速回放可视化工具？

> 原文：<https://dev.to/erjan_116/what-js-framework-to-use-to-make-stockmarket-simulator---speed-replay-visualization-tool--5fc1>

我想制作我自己的桌面股票模拟器，回放历史股价走势。

我有一个 CSV 格式的时间序列价格数据样本数据集。

本质上，我只需要在画布上呈现这些数据。主要是用更少的时间积累更多的交易经验。用户可以在一周内加速全年的交易！

我制作了一个用 Delphi(非开源)制作的另一个程序的 gif 来演示我想要构建的程序。

下面是展示我想要构建的内容的 gif:

[https://thepractical dev . S3 . Amazon AWS . com/I/a3 dkn 2 smu 41 zunxbyrv 5 . gif](https://thepracticaldev.s3.amazonaws.com/i/a3dkn2smu41zunxbyrv5.gif)

我认为我的项目与数据可视化有关。

这项任务似乎很简单，毕竟它只是解析如下所示的数据集，并在屏幕上显示每一个新的价格变动行。

日期开盘价-最低价-收盘价

*   10/07/2016 - 1.4 2.3 0.7 1.5 400
*   10/07/2016 - 3.4 1.3 23 1.4 5500
*   10/07/2016 - 1.7 2.3 0.9 1.4 100

高质量的分笔成交点数据显示每毫秒的变化，因此它有更多的字段，而不仅仅是“高开低走”，所以我想需要一些毫秒时钟计数器来反映价格的每一个变化。

画布应该具有:

当价格超出画布范围时，自动缩放以适应整个价格范围-所有条形都应相应调整其大小，
放大\缩小
速度调整滑块以降低/提高绘图速度
它是否类似于一些开源图形设计绘图工具？

应该用 D3.js，python，C++，electron.js 还是其他什么 js 框架？你能给我应该研究的方向或工具吗？
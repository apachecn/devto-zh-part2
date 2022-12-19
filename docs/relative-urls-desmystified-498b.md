# 相对 URL 去神秘化

> 原文：<https://dev.to/denmch/relative-urls-desmystified-498b>

真正理解相对 URL 的第一个关键是认识到它们指的是当前 URL，并不反映磁盘上实际的文件夹结构。所使用的符号类似于文件导航，但是在这个上下文中，您并没有遍历物理结构:浏览器使用一组简单但非常健壮的符号符号从当前 URL 值构造新的 URL。

让我们来看看一个方便的表，然后我会深入研究。确切地说，有四个不同的符号具有非常精确的含义:

| 标志 | 意义 | 笔记 |
| --- | --- | --- |
| `/` | 根 | 直到基本 URL |
| `//` | 草案 | 要避免 |
| `./` | 当前目录。 | 别名:无斜线 |
| `../` | 父母 | 可以合并 |

这些符号仅仅由斜线和点组成，单独或成对。乍一看可能有些混乱，但是前三个是不变的，不能组合。最后一个，有两个点，可以结合起来，我们将在下面看到。

## 2 斜线还是不 2 斜线？

将相对 URL 符号中的双斜线和单斜线概念化的最简单方法是认识到基本 URL 是内核，并将双斜线和单斜线视为类似于 bookends 的东西。一个将基本 URL 与其协议分开，另一个将它与其子页和目录分开:

| 草案 | 定界符 | url 基准 | 定界符 | 子页面等。 |
| --- | --- | --- | --- | --- |
| https: | // | dev.to | / | 丹奇 |

双斜线将告诉浏览器在基本 URL 之前构建一个 URL，回到协议。单斜线本身告诉浏览器在子页面和目录级别上，在基本 URL 之后构造一个 URL。

给定 URL `https://dev.to/denmch`，双斜线(`//`)是`https://`的简写，单斜线(`/`)是`https://dev.to/`的简写，字面意思是告诉浏览器从这个或那个不同的分隔符开始。

## 被认为有害的协议

毫无疑问，你已经使用一个`//path-to.my/script.js`形式的 url 链接到或者至少看到了没有规定协议的外部资源(`http:`或`https:`)。

这在一段时间内看起来很不错，但现在[被认为是一种反模式，可能会暴露漏洞](https://www.paulirish.com/2010/the-protocol-relative-url/)。尽管它可能是最好的避免方式，但是知道它为什么以这种方式工作是有好处的，并且它帮助我们更深入地理解相对 URL 符号实际上是如何工作的，特别是因为它仍然存在(即使我们应该避免它)。

## 点点我父亲的名字；叫我多特

斜线本身指的是**基 URL** 周围的书挡，*单条斜线与点*的组合指的是完整的**当前 URL** 并从右向左移动。

点限定符告诉浏览器*这个*斜杠是*而不是*根。语义上，一个点后面跟着一个斜杠(`./`)意味着“从当前目录开始”在任何其他组合中都不会出现`./`符号(例如，`.././`将无效)。

一个双点后面跟一个斜杠意味着“向上启动一个目录”，这个模式可以被复合为在当前 URL 中向左遍历，这样`../`引用当前目录的父目录，`../../`引用父目录的父目录，依此类推。

如果相对 URL 引用的“层代”多于当前 URL 包含的层代，则新的结果 URL 将尽可能向后开始:在基本 URL:

给定 URL `https://dev.to/denmch`，以下模式都返回到基本 URL ( `https://dev.to`)，因为没有父目录可以从当前 URL 推断:

*   `../../../`
*   `../../`
*   `../`

最后重要的一点是要认识到`./`有一个别名:以一个既没有点也没有斜线的相对 URL 开始。给定当前 URL `https://dev.to/`，形式为`href="denmch"`的相对 URL 在功能上等同于`href="./denmch"`，并产生最终 URL`https://dev.to/denmch`。

现在，由您来决定何时何地使用相对 URL 是有意义的，希望您能够更好地考虑和理解出现的问题和潜在问题。
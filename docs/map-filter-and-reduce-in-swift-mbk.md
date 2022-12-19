# 在 Swift 中映射、过滤和减少

> 原文：<https://dev.to/eleazar0425/map-filter-and-reduce-in-swift-mbk>

像许多现代语言一样，Swift 实现了一些漂亮的核心功能。如果您不熟悉函数式范例，通常可以实现经典的 for 循环来解决常见的集合类型问题，但这不是最快的方法。所以今天，我要介绍高阶函数，当集合类型加入时，它会让你简化代码。

高阶函数是接收其他函数作为参数的函数，或者是返回另一个函数作为结果的函数。在这篇文章中，我们将使用映射、减少和过滤。我们开始吧！

## 地图

> 在许多编程语言中，map 是高阶函数的名称，该函数将给定函数应用于函子的每个元素，例如列表，以相同的顺序返回结果列表。来源:维基百科

map 函数不会编写 for 循环并将您的业务逻辑应用于每个元素，而是为您处理这些。只需要编写将用于每个元素的函数，这样可以节省我们的时间和代码。

例如:
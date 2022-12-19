# 限制 R 包开发中的依赖性

> 原文：<https://dev.to/sckott/limiting-dependencies-in-r-package-development-2khf>

你做一件事的时间越长，你对这件事的偏好就越多。其中之一就是制作 R 包。

我开发的一个偏好是在我维护的包中限制包依赖性——或者至少限制到最不痛苦的依赖性。理想情况下，如果一个基础 R 解决方案可以完成，那么就这样做。如果每个人都在使用 R，他们都有基本的 R 包，所以你不能失败，至少在包的安装上。

这在很大程度上与信任单个软件包无关(参见杰夫·莱克的文章)，但是信任在决定使用哪个软件包时确实起了作用(参见*在做同样事情的软件包中选择*)。

### 为什么？

在这个问题上肯定会有不同的意见，但这就是我为这座山辩护的原因:

*   如果可以避免，为什么要引入更多的复杂性？
*   这又是一件你无法控制的事情。当然，在一个完美的世界里，软件包 API 永远不会中断，至少在某个版本(v1 左右)之后，但是我们不能依赖它。
*   为一个问题推出你自己的解决方案(又名函数/类/等等。)意味着它完全在你的控制之下
*   外面有很多很棒的软件包。然而，在我看来，许多软件包，包括我自己的许多软件包，都是针对交互式用户的，没有必要为其他软件包进行优化。所以即使一个包可以很好地完成 X，如果足够简单的话，你也可以自己完成 X。

### 基本分辨率

一些我喜欢使用而不是使用现成产品包的 base R 解决方案示例:

*   从列表中删除`NULL`元素。函数`function(l) Filter(Negate(is.null), l)`原本是从`plyr::compact`偷来的。我将它作为一个实用函数包含在我的许多包中。这是简单的基础 R 材料。很简单。
*   根据模式从另一个字符串中提取字符串。函数`function(x, y) regmatches(x, regexpr(y, x))`是`stringr::str_extract`在转向包装`stringi`函数之前所做的事情。我首先喜欢输入的模式，其次是您的模式，但是如果我知道我只需要一个简单的字符串提取，我不想导入一个巨大的依赖项(`stringi`)。
*   中缀功能`%||%`。本来在`dplyr`看到这个，现在已经离开那个包了。`function(x, y) if (is.null(x) || length(x) == 0) y else x`的功能。当您不能确定结果时，它提供了一个优雅的就地定义默认值的解决方案。这是一个非常简单的函数，所以不需要为这个函数导入一个包。
*   检查参数输入的类型是否正确。r 不像其他语言那样有类型检查。不过，我们可以在软件包内部完成。有一些包可以做到这一点(查看 [assertr](https://github.com/ropensci/assertr) )，但是我没有导入一个包，而是做了如下的事情:

```
assert <- function (x, y) {
  if (!is.null(x)) {
    if (!inherits(x, y)) {
      stop(deparse(substitute(x)), " must be of class ",
          paste0(y, collapse = ", "), call. = FALSE)
    }
  }
} 
```

这似乎很简单，我不认为进口一个软件包是值得的。

### 在做同样事情的包中选择

*   在我的包中，我经常需要将许多行/列表组合成一个 data.frame。`dplyr::bind_rows`和`data.table::rbindlist`这样做(可能还有其他人)。我发现`data.table`是一个稍微容易一点的依赖 WRT 安装，所以我通常使用下面的函数将命名列表绑定到一个`data.frame`的行中，并可选地转换成一个`tbl_df`。

```
function(x) {
  tibble::as_tibble((x <- data.table::setDF(
    data.table::rbindlist(x, use.names = TRUE, fill = TRUE, idcol = "id"))
  ))
} 
```

### 其他位

*   [Jim Hester](https://github.com/jimhester) 做了一个关于 [glue](https://github.com/tidyverse/glue) 包的演示:[用 Glue](https://rawgit.com/jimhester/presentations/master/2018_07_13-Glue_strings_to_data_with_glue/2018_03_28-Glue_string_to_data_with_glue.html#/glue-is-for-packages) 将字符串粘合到数据上——并在一张幻灯片上强调`glue`是针对包的，因为它没有依赖性，是可定制的，并且快速——所有你想要的东西都在你自己的包的依赖性中。
*   当我结束这篇文章时，我发现了一些文件:
    *   Claes et al. <sup id="fnref:1">[1](#fn:1)</sup> 发现“在三个月的时间里，CRAN 包中出现的错误…主要是由包的依赖关系的更新引起的…”
    *   在另一篇论文中，Plakidas et al. <sup id="fnref:2">[2](#fn:2)</sup> 扩展了先前的发现，并且说“……这潜在地暗示了当包维护者依赖于频繁更新的包时，他们的工作负担会很重”
    *   这些陈述反映了我对依赖其他包的犹豫，如果事实上 X 任务可以在内部完成的话

*   贡献者:如果您编写自己的内部函数，或者从别处借用，那么您的包的新贡献者可能需要理解您的内部函数，而不是从另一个包中导入的函数——但是好的一面是，如果函数驻留在您自己的包中，您可以很容易地对其进行更改。

*   快速开发阶段:通常包开发包括一个快速变化阶段，在这个阶段你想先得到一个工作原型，然后再进行细化。在这个开发阶段，使用现成的包让事情正常运行是有意义的。稍后，您可能想要交换包或编写自己的 R 或编译代码来加快速度，或者引入不同的行为，等等。

### 但是

当然，有很好的理由只导入最擅长 X 或 Y 的包，并让它保持原样。有时候我也这样做。我不总是呆在我的山上。

也许我完全错了？也许我应该一直使用其他包来做 X，Y 和 Z？尽管我有几十个包，但我完全知道我可能完全错了。

* * *

感谢[malle Salmon](https://masalmon.eu/)对这篇文章的有益建议！

### 参考

Claes，m .，Mens，t .，& Grosjean，P. (2014 年)。起重机包装的可维护性。2014 软件进化周- IEEE 软件维护、再工程和逆向工程会议(CSMR-WCRE)。【https://doi.org/10.1109/csmr-wcre.2014.6747183】↩

k .普拉基达斯、d .沙尔和 u .兹敦(2017 年)。软件生态系统的进化:度量、关系及其对质量的影响。系统与软件杂志，132，119–146。【https://doi.org/10.1016/j.jss.2017.06.095】↩
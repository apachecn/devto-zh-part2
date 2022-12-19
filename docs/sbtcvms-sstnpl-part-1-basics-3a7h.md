# SBTCVM 的 SSTNPL，第 1 部分:基础知识

> 原文：<https://dev.to/thomasthespacefox/sbtcvms-sstnpl-part-1-basics-3a7h>

SBTCVM 和任何平衡的三进制计算机一样，不同于二进制计算机，不管是不是虚拟的，它都有很多不同之处，使得现有的语言无法与之兼容(没有大量的工作)

鉴于此，我最终为它创建了第二种编程语言，称为 SSTNPL，或 SBTCVM 简化三进制数字编程语言。这是一系列关于它的使用以及使用它的最佳实践的教程的开始。

在第 1 部分中，我们将看看如何在两种类型的菜单中使用“keyprompt”命令来创建一个简单的程序，让用户更改布尔值。

## 入门

你需要的第一件东西是 SBTCVM gen 2-9，SBT CVM 的最新和最伟大的迭代，除了其他东西之外，还有 SSTNPL 的编译器。

一旦有了这些，您就可以继续创建*。VMUSER 目录中的 stnp 文件。(注意:如果您在。带‘auto _’的 stnp 你也可以把它放在那里的子目录里)

但是对于本教程，我建议从下一节中嵌入的 gist 下载示例程序，并将*。VMUSER 中的 stnp。

## 代码
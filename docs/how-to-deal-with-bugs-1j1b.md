# 怎么处理 bug？

> 原文：<https://dev.to/rlxdprogrammer/how-to-deal-with-bugs-1j1b>

# 简介

bug 是程序员日常工作的一部分。每个人都讨厌他们:测试人员、开发人员、经理和客户。所以很明显，它们应该尽快被移除。但是最有效的方法是什么。我仍然记得，在我职业生涯的开始，我需要在一个相当复杂的系统中找到一个 bug 并修复它，我完全迷失了。所以在帖子里我会和大家分享我的“猎虫”之道。

# 猎虫前

所以第一步是在理解的层面上:你应该理解什么是程序员的正常行为，你应该理解什么是 bug 本身，以及为什么 bug 行为是不正确的。

作为下一步，你应该能够重现错误。不重现问题，就不要开始寻找根本原因。也有可能该错误根本没有出现在您的系统上。在复制阶段，始终确保以下几点:您测试的代码版本与出现错误的版本相同，您使用的是相同的操作系统，所有设置都相同，所有其他条件都相同。

所以如果你想记录一个错误，一定要写下重现错误的步骤，预期的行为，当前的错误行为，确切的软件版本，所有的软件设置和你的系统信息。

一旦你重现了你应该找到的 bug，从这一点上有两种方法。

# 寻找 bug

第一个我发现非常有效的方法是基于代码的版本控制。您应该找到错误仍然不存在的最后一个版本。一旦你发现了它，检查一下在最后一个工作版本和第一个有问题的版本之间发生了什么变化，通常你会立刻找到根本原因。

下一个方法你真的需要从调试开始。您需要首先尝试识别包含 bug 的组件。为此，您将检查不同组件的输入和输出。一旦你发现组件试图向下一级:在类级，然后在函数级。

有些事情你需要经常考虑:如果你的代码中有多线程，考虑一下共享内存区域。如果有动态内存分配，总是要检查一下你是否用内存做了所有的事情。如果您使用第三方组件，请始终确保他们是否为您提供了正确的值。

使用像 gdb 这样的专业调试器软件，调试的持续时间会短得多。另一件可以使调试更快的事情是代码被单元测试覆盖。您只需要检查哪些单元测试失败了，这将引导您找到根本原因。

这些是我的基本练习，我认为通过练习会越来越快地找到错误，但是错误每次都会让你大吃一惊。

[http://howtosurviveasaprogrammer.blogspot.com/](http://howtosurviveasaprogrammer.blogspot.com/)
# 鲤鱼::总是有时

> 原文：<https://dev.to/jplindstrom/carpalways-sometimes-obk>

### 故障排除

你的程序刚刚死了。太好了，现在怎么办？

如果异常字符串以`\n`结尾，它不会给出一个行号
。但是即使这样，一个行号也不足以调试
问题。那就是问题发生的地方，但是我们是怎么到那里的呢？

[鲤鱼::总是](https://metacpan.org/pod/Carp::Always)来救援。

```
use Carp::Always; 
```

把它放在任何地方，所有的异常(和警告)都会有一个完整的
堆栈跟踪，包括子例程参数。

### 但是等等...

您可能不想在整个程序中永久打开它。使用`Carp::Always`是一个全局的、进程范围的改变，堆栈跟踪将被添加到所有异常的*中，甚至在`eval BLOCK`中。这可能不是你想要的。*

因此，由于它是一个临时的调试工具，在代码库中忘记它是一件非常糟糕的事情，因为它改变了全局行为 T2。

你知道吗，既然异常看起来会有所不同，那么在你的整个应用程序中没有什么会变得奇怪？不，你没有。因此，在同一行放上一个你可以“grep”的
提醒评论:

```
use Carp::Always; ### TODO: MyInitials: Remove before committing 
```

是的，它需要有你名字的首字母，移除它是你个人的责任。

### 防止失误

这种低调的提醒自己不要搞砸的方式可能还不够。毕竟程序员也是人，人总是会忘记事情，搞砸事情。你甚至可能是他们中的一员。

*如果这对你来说是个问题*你可以采取几种方法，例如

*   在源代码管理系统中提交钩子，防止它们被签入
*   在源代码树中寻找任何`use Carp::Always;`语句的自动化测试

### 特设鲤鱼

还在担心在使用声明中留下问题吗？您也可以在命令行上使用
来加载模块

```
perl -MCarp::Always script.pl
prove -MCarp::Always -r t 
```

只是为了脚本调用。或者，为了使它半永久化，用这个选项设置 PERL5OPT 变量:

```
export PERL5OPT=-MCarp::Always
perl script.pl 
```

记住:`Carp::Always`，但不是所有时间！
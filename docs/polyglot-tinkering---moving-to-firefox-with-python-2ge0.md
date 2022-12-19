# 多语言修补——用 Python 移植到 Firefox

> 原文：<https://dev.to/peteraba/polyglot-tinkering---moving-to-firefox-with-python-2ge0>

这篇文章最初出现在我的博客上。

### 火狐？

2002 年春天，IE6 发布后不到一年，我开始从事 web 开发工作。对于那些曾经听说过 IE6 的人来说，很明显这意味着我花了大量的时间来解决 IE 的各种怪癖，当然，在我的生命中，我曾经是火狐的超级粉丝。Firefox 在当时是惊人的，但不幸的是，随着每次迭代，它变得越来越慢，到谷歌 Chrome 出现时，大多数 web 开发人员已经准备好更快的东西了。从那以后，我使用了相当多的浏览器，但我总是因为这样或那样的原因回到 Chrome，我的大多数同事也是如此。

我有点怀疑，但也对 [Rust](https://www.rust-lang.org/en-US/) 和 [Servo](https://servo.org/) 感到兴奋，新的 Firefox 一稳定下来，我就试用了它。我喜欢它的速度和许多特性，但是在 Linux 上我有两个主要问题:

1.  出于某种原因，几天后我没有声音了，它再也没有回来。
2.  LastPass 糟透了，因为复制密码功能似乎被破坏了。

所以我又回到了 Chrome，尽管我更喜欢尽可能地去谷歌化。

### LastPass？

好吧，让我们快进几个月，直到我读到[呼吁所有 web 开发者:这就是为什么你应该使用 Firefox](https://stories.jotform.com/calling-all-web-developers-heres-why-you-should-be-using-firefox-983f012d4aec) 并决定是时候再给 Firefox 一次机会了。这一次声音工作正常，但 LastPass 在复制我的密码时仍然有问题。当我打开一个存储有密码的页面时，输入字段已正确填写，但我无法轻松地搜索并复制存储的密码。

这对我来说是一个巨大的问题。

我希望我不用提到密码管理器有多重要，但是对我来说，自动填充是不够的。句号。我存储了大量的密码和笔记，我经常需要复制它们来访问各种东西，并且在我的 LastPass Vault 中打开一个详细页面太慢了，这不是一个可行的选择。

因此，此时我决定用 LastPass 创建我的第一张支持票。他们的反应很快，很简短，很令人失望。引用相关的片段:

> 我很抱歉地通知你，Linux 上的 Firefox 浏览器不支持二进制特性。
> 复制用户名和复制密码需要二进制特征。

嗯，我想这对大多数人来说只是意味着回到 Chrome，但我决定拿出一个工具来解决我的问题。我并不是想解决每个人的问题，也不是想在 Github 上做一些有明星和其他人参与的花哨项目。我想写一些快速而简单的东西，写一些有趣的东西，并且以一种我不再被阻止使用 Firefox 作为我的主要浏览器的方式解决我的问题。

### 澄清项目

以下是我的要求:

1.  我需要能够访问我的笔记和密码，而不是登录网站。(因为自动填充工作正常)
2.  该解决方案必须至少与使用 LastPass Chrome 扩展一样快:
    1.  意识到我需要输入密码才能完成工作
    2.  打开/转到 Chrome
    3.  打开 LastPass 浏览器扩展
    4.  搜索我感兴趣的记录
    5.  右键单击我需要的条目
    6.  复制便笺或密码

我的第一个想法是创建一个小的桌面应用程序，它位于我的系统托盘中，让我根据需要查找密码。然后我想，我真正想要的是有一个键盘快捷键来打开这个应用程序，这将允许我立即搜索。最后，我意识到我将从一个 CLI 应用程序开始，我将考虑一旦它在终端中工作，如何启动它。

### LastPass CLI

这个思考过程花了大约 2-5 分钟，与此同时，我找到了看起来我可以使用的东西 [lastpass-cli](https://github.com/lastpass/lastpass-cli) ，除了它需要多个命令调用来实现我想要的。

我测试了如何使用我的 shell (Bash / Zsh)解决我的问题:

1.  lpass 登录
2.  lpass ls | grep "我最喜欢的服务器"
3.  选择我想要访问的服务器的 id(使用鼠标)
4.  lpass 显示“我最喜欢的服务器的 id”
5.  将笔记或密码复制到剪贴板(使用鼠标)

```
my-favorite-server [id: 1112223334445556667]
Username: root
Password: my-super-safe-password
Hostname: 123.234.432.321:12345
NoteType: Server 
```

Enter fullscreen mode Exit fullscreen mode

好的，看起来我真的可以通过使用`lpass`、`grep`和`xclip`来做我需要的事情，但是如果有多个搜索结果，我还需要能够选择其中一个。现在，我碰巧是一个相当有经验的终端用户和`bash`程序员，而我从来没有做过系统管理员，但是说实话，一想到这个工具需要这么多脚本，我就觉得恶心，主要是因为在 Bash 中操作字符串很麻烦。在`zsh`要好得多，但大多数时候我需要坚持`bash`，因此我的 zsh-foo 相当基础。

### 找到合适的工具

好吧，如果不是，那是什么？嗯，这是一个非常简单的任务，几乎在我所知道的任何编程语言中都可以完成(`Elm`是个例外)，但是一开始我只考虑了我每天使用的那些语言，以使事情变得简单。然而，在这个任务中，我并不喜欢他们:

*   我觉得打包命令行界面调用有些臃肿，而且我的所有电脑上都没有安装它
*   因为它的类型安全，包装 CLI 调用感觉有点笨拙。
*   `JavaScript`不是我的竞争者，因为我不喜欢`Node`。

嗯，在上面的选择中，我会毫不犹豫地选择 bash，但是我记得系统管理员倾向于喜欢`Python`。我从来没有大量使用 Python，但是我确信我在栈溢出上比 Bash 做得更少，我更喜欢最终结果，并且它比我的主要语言更适合这个任务。

### 黑客是乐趣

我花了大约一个小时才拼凑出我需要的东西。我不得不承认，由此产生的代码并不值得我骄傲:

*   该脚本只能在 Linux 系统上运行
*   我甚至在开发过程中决定不创建函数，只是为了简单起见。(抱歉，不是抱歉。)
*   我确信无论是使用 Python 还是 Bash / Zsh，都可以在不到 20 分钟的时间内完成我所做的事情。

然而，使用 Python 被证明是一个爆炸，我认为最终结果是可读的，即使它缺乏真正的技巧。见鬼，黑客还是很好玩的！

作为一名程序员，最酷的事情之一就是你可以相对轻松地解决自己的许多问题。如果你花时间去思考那些你并不是每天都会用到的编程问题、原理和语言，那就更是如此了。Python 确实很棒，尽管我可能永远不会用它来做任何严肃的事情。

### 结果

如果这是你与我分享的一个痒处，请随意使用我写的脚本:[https://github . com/Pete raba/dot files/blob/master/scripts/LPS](https://github.com/peteraba/dotfiles/blob/master/scripts/lps)

为了提高效率，我建议使用类似地震的终端，比如 [Guake](http://guake.org/) ，这样只需击一次键就可以了。

使用这个脚本，我检索随机密码的例程如下所示:

*   意识到我需要输入密码才能完成工作
*   按 F12 打开 Guake(除非我已经在终端中)
*   类型`lps my-favorite-server`
*   通过输入一个数字选择一个结果，然后点击`Enter`(除非只有一个结果)

此时，脚本告诉我，笔记或密码已经复制到我的剪贴板。这比使用 Chrome 扩展要快得多，每天至少节省 1-2 分钟。更重要的是，我现在可以完全接受任何新的浏览器，LastPass 扩展的缺乏不应该再次阻止我。
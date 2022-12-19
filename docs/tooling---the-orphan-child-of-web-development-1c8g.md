# 工具 web 开发的孤儿？

> 原文：<https://dev.to/martinhaeusler/tooling---the-orphan-child-of-web-development-1c8g>

# 在一次开发会议中...

尽管我认为自己主要是一名后端开发人员，但有时我会尝试涉足前端领域，并与 HTML、CSS 和 JavaScript 世界中发生的事情保持联系。在这种情况下，我最近参加了一个当地的开发者聚会，并参加了一些非常精彩的演讲。

其中一位演讲者(全职 react 前端开发人员)正在展示 React 16 中的一些新功能，并对其中一些功能进行了现场演示，在 WebStorm 和浏览器之间来回切换。在问答环节，我忍不住问他是否可以打开他的 JSX 文件的结构视图一会儿(我想看看是什么样子)。他奇怪地看了我一眼，所以我告诉他在 IDE 中的什么地方点击。当面板弹出时，他说

> “我从来没见过这个，那是什么？”

我坐在观众席上，困惑不解，不知该说些什么。我个人不使用 WebStorm(由于订阅模式)，但我对 VSCode 的一个主要问题是它*仍然*没有提供一个适当的大纲/结构/符号树视图(有一个[插件](https://github.com/patrys/vscode-code-outline)，但它非常基本)。我认为这种观点对于处理更大的代码库是必不可少的。这个前端开发者站在那里，看着他的 WebStorm 窗口，不知道该怎么做。

# 工具跟不上步伐

JavaScript 框架最近像疯了一样不断出现。最新最好的 GUI 编写方式并不是你六周前一直在做的事情。习惯于 Java 的发布周期(尽管最近它也在加快步伐)，这种速度是疯狂的。现代 web 开发甚至不回避改变所用语言的语法(你好 [CSS Modlues](https://github.com/css-modules/css-modules) ，甚至 JSX 也是如此)。但是在整个过程中，似乎没有人关心编辑器对所有这些闪亮工具的支持。“记事本已经足够好了”的想法似乎在今天的 web 开发社区中根深蒂固。这与那些仍然既不使用[类型脚本](https://www.typescriptlang.org/)也不使用[流](https://flow.org/)的 JavaScript 开发者是一脉相承的——为什么会出现这种情况超出了我的理解范围。当然，对于一个 2000 LoC 的网页来说，这已经足够了。但是在我工作的领域，没有所谓的“小”应用程序。包含成千上万代码行的数千个文件是那里的日常事务。试图说服我，如果没有合适的工具，这些应该如何工作。我会等的。

> 如果每 100 个 JavaScript 框架中会出现一个像样的 IDE，网络世界将会是一个更好的地方。

# 但是我们确实有 VS 代码！

Visual Studio Code 的确是一个优秀的编辑器，我个人认为它是微软迄今为止发布的最好的编辑器。然而，尽管它可能很简洁，但它是一个*编辑器*。它不是一个 IDE。现在，我完全意识到有些人更喜欢编辑器(传说在某个地方住着一个部落的人，他们使用 [vim](https://www.vim.org/) 而不被强迫)。对所有这些人-对不起，但你来错了文章。

有一些特性对于在大型代码库中高效工作是绝对必要的(当然是以我个人的观点),这些特性将 IDE 与编辑器区分开来:

*   **代码完成**

我这里说的不是*字*完成或者*百猜*完成，而是实实在在的交易。随着语言服务器的兴起，甚至在编辑器中实现这一点也变得容易多了(至少对于强类型语言来说)。

*   **结构视图**

也称为大纲视图或符号树视图。当浏览代码库时，我甚至不想看到源代码，而只想看到结构，并且我需要能够快速浏览它以获得概览。

*   **类型层次视图**

想知道在你的整个代码库中有多少子类吗？IDE 可以按下按钮告诉你答案。“但是为什么你需要它呢，反正继承在 JavaScript 中是避免的”——这是另一篇文章；)

*   **重构**

尽管如今网络上的潮人脚本专家对此一无所知，马丁·福勒 **描述的[代码味道确实影响了他们以及软件工程行业的其他人。适当的重构工具是恰当处理它们的必要条件。](https://martinfowler.com/bliki/CodeSmell.html)**

*   **自动导入**

我不想每次都寻找我需要的课程的确切位置。IDE 足够智能，可以根据类名为我提供匹配的建议，并相应地添加导入。它还可以批量处理整个文件，同时删除所有不需要的导入。

> 这些是基本的 IDE 特性。这里我们甚至没有谈论更高级的结构分析的可能性。

好了，让我们看看我们亲爱的 vscode 如何实现这个列表。多亏了 TypeScript 和它的语言服务器，当涉及到代码完成的时候，它已经覆盖了你。我发现这个功能非常好用，没有任何抱怨。在结构视图上，如前所述，有一个第三方插件提供了非常基本的功能，但是，目前的 vscode 甚至不允许您重新定位屏幕上的单个视图面板，并且结构视图的当前默认位置是在屏幕的左下角——这不太理想。
类型层次结构在 vscode 字典中是一个未知单词。据我所知，也没有第三方插件。
重构呢？良好的...vscode **可以**处理重命名。大部分是。除非您重命名文件夹。或者移动文件。或者...好吧，让我们面对现实吧，目前重构 typescript 应用程序文件夹是一件非常痛苦的事情。如果你认为重构的范围是重命名和移动文件，那你就大错特错了。看看 IntelliJ 在 Java 的重构部门做了什么就知道了。*那个*就是我说的工装水平。
对于 TypeScript 来说，自动导入在 vscode 中是一把双刃剑。有些导入会被自动识别，有些则不会；我还不知道这到底是怎么决定的。有一个名为 [TypeScript Hero](https://github.com/buehler/typescript-hero) 的第三方插件，据说有整个文件的导入组织，但是我还没有试过。

因此，我对 vscode 作为一个 IDE 的结论是喜忧参半——虽然它在某些方面做得非常好(代码完成、流畅的文本编辑、快速启动),但它在其他方面肯定有缺点。就非商业工具而言，这似乎是我们目前所能做到的。

# 最后的话

从 enterprise Java 来到 Web dev 世界，我很困惑为什么没有更多的人开始寻求更好的工具支持。坦率地说，我对 web 开发人员如何构建大型应用程序感到惊讶，相比之下，他们配备的不过是由绑在石头上的棍子组成的临时锤子。而当被问到这件事的时候，他们会告诉你*“没关系，我不需要再多了”*。这只是背景和心态的问题吗？如果这些人知道他们能做什么，他们会想要更先进的工具吗？你对 web 开发的工具支持有什么想法？
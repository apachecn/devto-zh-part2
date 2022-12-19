# 鲁比历险记

> 原文：<https://dev.to/atxrenegade/adventures-in-ruby-4bm8>

# 红宝石历险记

## (或从创建 CLI Gem 中吸取的经验教训)

### 范围和概念

我最初的概念想法，带着我所有的热情和天真，是创建一个宏伟的通用开发人员参考，包括 atom、ruby 方法、cli 命令、pry 命令和任何其他 web 开发人员经常使用的工具的快捷方式。虽然这个概念很棒，但我花了几周时间浏览页面，试图找到任何可行的“备忘单”，既不是 pdf 格式，也不是 html 表格。最终我意识到，处理一页又一页的表格将会很乏味，几乎不可能解析和理解。我缩小了范围，在我选择的所有工具和网页中选择了最合适的表格，结果是 GitHub 上的 atom 快捷方式参考页面。

**经验教训:** MVP。最低可行产品。从小范围和小规模开始，在实现了一个完全有效且经过测试的 MVP 之后再进行扩展。一次做一个，在开始之前让每个部分都正常工作。对此要有耐心和自律。在一个代码块中找到一个 bug 要比以后在数百行代码中找到一个 bug 容易得多。

### 刮取和数据格式化

因为我选择从中删除对象数据的页面是表格式的，所以它确实需要大量的解析、调整、拆分和散列来为每个要传递到模型类中的对象创建一个散列值数组。我以为我已经解决了所有的问题，并且在项目进行到一定程度的时候，我注意到我注意到了奇怪的大写，并且缺少表值导致我的散列对象偏移，颠倒了键值对。我通过向数组中添加 n/a 值来解决这个问题，以便将属性放回正确的顺序和位置。回想起来，虽然我创建一个新的表很有挑战性，但我可能选择了其他更可靠的东西，并且通过使用 css 选择器更容易深入使用。

**经验教训:**在选择网站时，寻找有清晰 css 选择器格式的网站，并以系统有序的方式分解元素。

### 模型架构

[![](../Images/5b62a8fc5fd0b7bd03250f4c8b3d49cc.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--dXeD_apw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://i0.wp.com/www.brainpickings.org/wp-content/uploads/2013/01/chickenegg1.jpg%3Fw%3D300%26ssl%3D1)

这个特殊的话题似乎在我脑海中引发了最多的问题。有时我会困惑，直到我发现自己陷入了一个无限的循环，在循环中旋转，直到我找到了终点或起点。先有鸡还是先有蛋？鸡蛋是鸡的产物，还是鸡是鸡蛋的产物？开始无限循环。慌！利用我对所属关系、拥有关系、拥有关系和对象关系的理解，我坐下来写下了三种不同的构建模型的方法，并选择了一种感觉最自然的方法来实现我的应用程序的功能。我已经将该文档包含在我的项目文件中，并最终在决定当前配置之前，对其进行了重构，测试了另外两种架构安排。

### CLI 应用程序功能

我的 cli gem 的界面流将首先向用户简要介绍应用程序，然后是主菜单，用户将首先从列表中选择他们的操作系统。这将导致对 Scraper 的方法调用，然后 Scraper 将在网站上搜索所有快捷方式，将这个字符串数组传递给数据格式化程序类。DataFormatter 类将创建我的对象散列，这些散列被传递到用于对象创建的快捷方式模型中，并向用户返回子菜单。这个新的子菜单(搜索菜单)将包括一个列出所有快捷方式选项——它将在一个编号列表中显示用户选择的操作系统的所有 atom 快捷方式，一个按键搜索选项——它将允许用户搜索特定键序列的快捷方式。“ctrl-m”和一个按名称搜索的选项——允许用户按名称搜索 atom 快捷方式。“打开文件”。如果他们选择列出所有的快捷方式，他们将被给予从列表中通过数字选择快捷方式的选项，并且程序将返回他们选择的快捷方式的详细视图。详细视图包括快捷方式名称、按键顺序、操作系统以及快捷方式功能的简要描述。键入“X ”,然后按 enter 键，用户几乎可以从程序中的任何地方退出程序。

一旦创建了对象，并且创建了搜索和列表函数，我注意到 theta 并没有真正以任何顺序显示，所以我决定创建一个按字母顺序排列的函数，以便更容易直观地理解。

### 对象重复

[![](../Images/2721ee8dc8790ea3df70e2e59ff691d9.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--MI-9YjGL--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://www.vikrambedi.com/wp-content/uploads/2017/10/duplicate-content-image.jpg)

在测试我的列出所有快捷方式功能时，我发现了一个让我困惑的有趣的错误。我的第一个操作系统显示了所有正确的对象和值，而第二个操作系统返回了所有请求的对象和一个副本，第三个操作系统似乎返回了快捷方式对象的三个副本。然而在其他时候，这个程序似乎运行得完美无缺。这种不一致使我更加困惑。在写这篇文章的时候，我不知道是什么导致了这个错误，这是完成我的项目的最后细节。当我打这些信的时候，闪电来了，我有了一个“啊啊啊”的时刻。

[![](../Images/fe51b25cee54e44734cf86306e6bcdfd.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--DWEPeCKX--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://vignette.wikia.nocookie.net/buddyfight/images/d/d8/Homer-simpson-quotes-doh-i11.jpg/revision/latest/scale-to-width-down/304%3Fcb%3D20141227165956)

什么会导致在第一个操作系统中显示正确数量的对象，在第二个操作系统中重复显示，在第三个操作系统中重复显示？哦！这是否与我的 scraper 在操作系统被选择后被调用的事实有关，这意味着每次选择新的操作系统时都会调用它，每次调用 scraper 类时都会创建每个对象的另一个副本。我通过将 Scraper 类的方法调用从它在主菜单中的尴尬位置移到 CLIInterface initialize 方法来解决这个问题，该方法在每次程序执行时只被调用一次，这立即纠正了这个问题。

经验教训:熟悉对象的生命周期和程序中的事件顺序。强迫你清楚地说出错误、概念和问题，通常有助于在你自己的头脑中确定这些东西是什么。通常当我在一个概念上或者在调试过程中感到停滞不前时，我做的第一件事就是问自己——问题是什么？我到底想完成什么？有时通过澄清问题得到的答案因为容易定位，或被吸收。

这又是一次测试我解决问题能力的编程冒险，同时也让我意识到了盲点和语法错误。对我来说，建造自己的项目是实践、学习和保留概念的最有效方式，也是最有收获的方式。

点击此处查看 cli gem 的演示:
[https://youtu.be/5GZ8Ck5W3us](https://youtu.be/5GZ8Ck5W3us)

atx renegade/ha Leigh Abel
# 变色龙 v.12 发行说明

> 原文：<https://dev.to/devexperts/chameleon-v12-release-notes-53i5>

*以下发行说明报告了从 v.7 到 v.12 的完整变更日志。*

变色龙是一个强大的网络工具，用于在整个产品套件中创建和控制多种调色板。此版本包括几个期待已久的更新，具有许多新功能和性能修复。随着这个版本的发布，变色龙拥有了一大套稳定的基础特性，并为下一波改进做好了更好的准备。

第 12 版可通过以下链接获得:

[https://github.com/Devexperts/chameleon](https://github.com/Devexperts/chameleon)

**变更请求**

1.  在每个用户会话期间所做的更改现在是持久的。当用户开始新的会话时，退出用户会话时任何未提交的更改或选定的调色板都将被恢复。这些会话保存在用户设备的本地存储中。“保存更改”按钮已被重命名为“提交更改”以反映这一新功能。
2.  所有更改在提交前都会突出显示，以便在保存到服务器之前更容易识别当前的颜色更改。
3.  最后，我们在“选择调色板”窗口中添加了删除和重命名按钮，以帮助管理 UI 空间中的混乱。在这种情况下，删除实际上执行的是存档操作，因此变色龙服务器上的信息不会丢失。
4.  你现在可以通过点击“火焰”图标来删除“编辑变量”窗口中的任何颜色🔥。它从调色板中移除颜色，但不会自动将此更改提交给服务器。该颜色会突出显示为未提交的更改。
5.  现在对颜色和不透明度的输入和验证有了更好的支持。无效的输入数据现在以红色突出显示。增加了颜色代码的自动完成。

**改进**

1.  布局更适合小屏幕，小到平板电脑大小。现在，页面宽度可以降低到 780 像素，而不会影响工作效率。两个打开的应用程序可以使用一个显示器。
2.  单击“提交更改”后，性能显著提高。
3.  现在使用扩展布局，填充空间减少，调色板空间增加。
4.  主导航的小调整。导航按钮组合在一个固定的标题中。滚动调色板不会阻止对主要功能的访问:选择新调色板、添加变量和提交更改。
5.  一个更友好的变色龙用户界面外观。

**bug**

对导入外部调色板和将颜色更改保存到服务器的小修复。
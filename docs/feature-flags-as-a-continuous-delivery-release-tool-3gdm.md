# 将标志作为连续交付发布工具

> 原文：<https://dev.to/iedaddy/feature-flags-as-a-continuous-delivery-release-tool-3gdm>

> "功能标志对于风险缓解、快速反馈、假设驱动的开发还是订阅层更好？"

是的。

[![](../Images/0abf7d1365312930ca314e582a17315b.png)T2】](http://iedaddy.com/wp-content/uploads/2018/02/feature_toggle.png)

功能标志可用于在最终产品中启用许多不同的行为，它们可以让产品所有者在整个开发生命周期以及面向客户的产品中对产品的行为和用户可访问性进行细粒度的控制。它们是在整个开发和交付过程中推动更有效的开发运维并推动创新的宝贵技术。

常见的功能标志类型包括:

## 切断开关

[![](../Images/98e17fe985ec89b6909c59a4a93cab8d.png)T2】](http://iedaddy.com/wp-content/uploads/2018/02/reb_button.jpg)

特性标志是代码中的一个条件，是两个不同选项的 IF/THEN。

最简单的，一个特征标志可以用来标记一个新的或危险的行为。kill switch 的伟大之处在于，它们可以在产品中独立于部署使用。

您可以随时打开新功能。如果该功能没有按预期运行，可以很快将其关闭。这允许继续开发其他功能，而不必强制完全回滚您的生产代码。

借助功能标记，您可以通过封装和控制每个功能来降低风险，这样，如果某个功能在生产中出现问题，就可以将其关闭，而不是回滚部署。

## Beta 反馈/金丝雀发布

[![](../Images/8bbb6ef5c3e2da57025a76d17920bd53.png)T2】](http://iedaddy.com/wp-content/uploads/2018/02/canary_coalmine.jpg)

为了获得更快的反馈，除了开/关开关之外，您还可以在非常精细的级别上控制谁能看到新功能。这允许你向一群“友好”的高级客户展示一个新特性，这些客户愿意尝试你正在开发的一些新特性。这些 beta 测试人员可以审查特性，并尝试一下，给你很好的反馈，这些反馈可能是在构建产品的原始用例时没有考虑到的。

## 假设驱动开发& A/B 测试

[![](../Images/23b72f7060757ec6527fe94e18acaf6f.png)T2】](http://iedaddy.com/wp-content/uploads/2018/02/hypothesis.png)

假设驱动的开发特性标志对于长期的访问级别控制也是很好的。它们能够根据某个功能是否对一组用户启用来衡量最终用户的行为，并衡量他们的行为，从而帮助证明某些指标。例如，如果您有一个只有高级用户才能访问的功能，您可以使用一个功能为“新手”和“高级用户”提供不同的体验。

您还可以使用功能标志来控制本地化，由于世界各地的法规各不相同，您可能会发现需要在一个国家启用功能，而在其他国家禁用功能，以便符合该特定国家的法规要求。

## 订阅计划和权限切换

[![](../Images/887e661abf9e30b406cb28391f105502.png)T2】](http://iedaddy.com/wp-content/uploads/2018/02/subscribe-300x300.jpg)

您可以将几个标志捆绑在一起形成一个订阅，例如，您可以拥有一个青铜级、白银级和黄金级，并根据与他们的帐户绑定的订阅，启用每个订阅计划可能为他们提供的各种功能。这是许多“免费增值”应用程序订阅的模式，每个人都有权访问一组基本功能，但其他功能只为付费群体的客户保留。

## 管理特征标志的技术债务

特征标志有迅速增加的趋势，尤其是在首次引入时。Toggles 需要被视为技术债务，它们会带来持有成本，因此防止它们在应用程序中扩散也很重要。

[![](../Images/867ffc9888f1d582cd150655e1e1bfb7.png)T2】](http://iedaddy.com/wp-content/uploads/2018/02/technical-debt.jpg)

为了保持特性标志的数量可控，团队必须主动移除不再需要的特性标志。一旦某个特定的金丝雀功能在生产中启用并被证明是稳定的，它就应该被删除并过期。其他技术可能包括通过限制系统允许拥有的特性标志的数量，将治理添加到开发规则中。一旦达到限制，为了添加另一个功能标志，您需要检查当前设置并删除一些现有的标志，以便在上限下腾出空间。

*post[Feature Flags 作为持续交付发布工具](http://iedaddy.com/2018/02/feature-flags-release-tool/)最早出现在[一个内陆帝国老爸](http://iedaddy.com)的经历上。*
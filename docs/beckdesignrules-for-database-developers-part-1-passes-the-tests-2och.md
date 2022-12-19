# 数据库开发人员的 BeckDesignRules 第 1 部分:通过测试

> 原文：<https://dev.to/pesse/beckdesignrules-for-database-developers-part-1-passes-the-tests-2och>

软件设计和软件架构是有时与遥远的、有点疯狂的天才联系在一起的主题，这些天才生活在象牙塔中，定期向他们的“普通”开发人员的地勤人员扔 UML 图。它们被视为神秘的知识，只有最有经验、最有才华的“ [10x 开发者](https://dev.to/nathanepstein/what-is-a-10x-programmer)”、“摇滚明星”和“忍者”才能吸收。

从我的经验来看，这种观点与现实相去甚远。相反，我认为软件设计和架构是任何开发工作的基础部分。从我们开始写代码的那一刻起，我们就会做出决定，并且正在创建软件设计，不管我们是否意识到。当然，可能会有指导方针，可能会有其他人给出的架构，甚至可能会有详细的 API 描述和描绘大画面的抽象设计，但最终日常的小决策将对结果产生巨大影响。

因此，理解好的软件设计的规则是一个影响任何技能和经验水平的开发者的话题。那个领域的知识对于每一个与软件开发相关的任务都将是极其有益的。

# 简单设计的四大法则

极限编程(XP)和测试驱动开发(TDD)的开发者 Kent Beck 在 20 世纪 90 年代末提出了简单软件设计的四条规则， [Martin Fowler](https://martinfowler.com/) 这样表述:

[![BeckDesignRules](../Images/73dd36715c0185f3831823bfb362d2f6.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--q4yxPRtY--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://cleandatabase.files.wordpress.com/2018/06/beckdesignrules.png%3Fw%3D676)

Martin 在他的文章中对“ [BeckDesignRules](https://martinfowler.com/bliki/BeckDesignRules.html) ”做了一个很好的、容易理解的描述，这也是上图的来源。

我将尝试深入研究这些规则、它们的精神以及它们在数据库开发中是如何实现的。我这边也有很多个人的解释，我不完全确定肯特·贝克是否会同意我所有的想法(当然我希望如此)。

我将把这篇文章分成几篇博文(你不会相信保持我每月一篇博文的个人目标有多难)，今天的博文将涵盖第一条，可能是最重要、最有影响力的贝克设计法则:

# 通过测试

这显然是关于单元测试，测试驱动开发和你的测试报告中的许多绿灯，不是吗？这意味着好的软件设计必须采用来自 XP 或其他敏捷方法的特定模式，对吗？虽然我不知道肯特·贝克提出这些规则时到底在想什么，但我认为这种解释太短视和狭隘了。因为如果我们谈论通过测试，我们首先必须考虑测试:

软件必须通过哪些测试？有什么要求？我的软件，我的函数，我的代码应该做什么？

突然，我们离开了关于框架和方法的教条的、技术性的讨论，进入了“业务知识”或“领域知识”的领域。这是我们定义“测试”的来源。这是将提供最大价值的层。

毕竟，我们的软件是为了解决一个特定的问题而存在的，这个问题很可能是一个商业问题。不管我们使用哪种敏捷方法、哪种数据库管理系统或哪种语言，如果没有关于问题及其环境的知识，我们解决问题的机会最多也是有限的。

[![A rewrite will end up with the same problems as the original unless you close the understanding gap](../Images/01d1fe105363891b8dd26c6b1523b2a7.png)T2】](https://twitter.com/PeterHilton/status/1006928030240071680?ref_src=twsrc%5Etfw)

作为开发人员，我们最重要的任务之一就是消除这些理解上的差距，了解问题的领域。

因此，我们的职责不仅是学习算法、范式和索引策略，还要了解我们的客户，提出问题，并采纳最终将使用我们软件的人的观点。

这还不够:作为数据库开发人员，这还意味着我们不仅需要理解我们的数据模型，还需要对使用我们数据库的应用程序如何工作有足够的了解。

如果我们设计了一个模型或者创建了一个应用程序无法使用的功能，这不是“那个愚蠢的应用程序开发者的错”，而是我们缺乏领域知识。

也是我们整个团队的失误。

即使我们认为功能或模型是潜在问题的良好解决方案，并且应该在应用程序中进行更改，我们也有责任以一种感同身受和可理解的方式传达我们的观点。

## 测试定义

如果我们对这个问题有足够的了解，我们就可以开始定义我们的软件需要通过的测试。这个定义可以类似于敏捷方法中对 done 的[定义，一个正式的合同规范或我们与客户达成一致的功能需求(尽管在大多数日常问题中不会足够详细),或者只是我们头脑中的一幅图画，这取决于具体情况。](https://www.agilealliance.org/glossary/definition-of-done/#q=~(filters~(postType~(~'page~'post~'aa_book~'aa_event_session~'aa_experience_report~'aa_glossary~'aa_research_paper~'aa_video)~tags~(~'definition*20of*20done))~searchTerm~'~sort~false~sortDirection~'asc~page~1))

问题或功能越复杂，以某种方式写下定义和测试就越有益。它们可以写成单元测试，正式的[合同设计](https://en.wikipedia.org/wiki/Design_by_contract)规范，也可以写成维基页面上的需求列表。

写下事情也有助于增加你的领域知识。

特别是在处理遗留代码时，我发现逐行分析现有代码并以非代码的方式写下来非常有帮助。在那之后，我经常可以更容易地识别逻辑问题和提取测试定义，特别是如果要处理的遗留代码非常冗长和“增长”的话。

当然，有些方法比其他方法更有优势，但是从我的经验来看，不考虑环境而强行追求一个特定的方法不会有什么好处。团队有不同的经验，项目有不同的成熟度和质量，公司有不同的可用预算和既定的文化。如果有必要，我们可以一步一步来。最重要的是开始走路。

## 通过所有测试

“通过测试”中没有“一些”。Beck 的设计规则包含了对质量的强烈要求，因此我们的软件或功能必须通过所有的测试。这不仅包括它应该做的事情，还包括应该**而不是**发生的事情。

不受欢迎的行为总是会让用户感到沮丧(并因此失去公司拥有的最有价值的货币:信任)。但是，尤其是在数据库开发的环境中，不必要的或意想不到的行为可能会导致严重的后果，如数据丢失或数据损坏——这些事情在事后很难修复。

“通过测试”伴随着对错误行为的零容忍态度，因此提出了可能出错的问题。如果我们得到一个负数呢？如果某一列为空怎么办？如果选择不返回任何行怎么办？如果它返回不止一个呢？

我们可能已经定义了软件的“快乐路径”，但是处理不想要的输入或状态的后果同样重要。

## 限制范围

我们突然处于这样一种情况，曾经简单的需求变成了边缘案例、可能性和必需测试的巨大怪物。我们正面临着许多不确定性，在考虑了所有需要覆盖的测试之后，我们甚至可能想扔掉所有关于好的设计的废话，只是“完成工作”。

虽然在某些情况下，这可能是一种实用而合理的方法，但在大多数情况下，这将是一种为了现在的快速成功和将来的巨大维护成本而进行的交易。

然而，有一些可能性来处理突然增加的工作量，其中之一就是限制范围。

> 一个设计师知道他已经达到了完美，不是当没有什么可以添加的时候，而是当没有什么可以拿走的时候。
> 
> *—安东尼·德·圣埃克苏佩里*

定义你的软件应该做什么，并缩小范围。

如果你的软件管理帝国军成员的休假，它不一定需要能够管理叛军(可能完全不同)的休假规则——如果有的话。

它绝对不需要了解西斯的历史(即使有些国定假日是以最强大的西斯命名的)。如果我们不太可能同时向帝国和叛军出售我们的软件，我们就不应该从成千上万的抽象和配置选项开始，来支持那个遥远星系中每一方的特定休假规则。

有些功能是无可争议的，因为它们是客户强烈要求的，或者是解决现有问题的关键。但是有些问题(尤其是包含高度不确定性的问题)可能会被推迟，直到我们对问题领域有了更好的理解，这将导致更好的决策。其他的可能属于 [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it) (你不需要它)，可以完全跳过。

渴望降低复杂性！如果没有必要用更复杂、更通用的方式去做，那就不要做。如果你增加了知识并掌握了基本的挑战，你总是可以在以后增加复杂性。但从第一天开始，你将很难采用成熟的方法。而且很有可能你最终得到的软件包含一堆未经测试的特性和一堆没人需要的特性——特别是如果前者不能正常工作的话。

## 数据库的力量

还有另一种可能来处理所需的努力:限制不确定性。

我们数据库开发人员有非常强大的工具来做到这一点:关系模型和约束。这两者都是我们数据库中固有的自然范围限制器。你希望某一列有一个特定的范围？通过创建约束来确保这一点。你认为一天的假期是属于一个帝国士兵的吗？使用不同的表和外键约束将此规则固定下来。

我之前提到过设计合同。每个成熟的 RDBMS 都内置了使用它的功能(至少在某种程度上)。

有些约束(尤其是涉及不同表的约束)创建起来更复杂，但是工具是可用的。只要你有可能消除不确定性，就去做吧！它限制了复杂性以及可能出错和需要处理的事情。

我曾经分析过一个数据库，它除了主键之外不包含任何约束，当我问开发人员为什么时，他们告诉我他们会通过中间件内部的“hibernate constraints”来保证一切。没过多久，表格中就堆满了损坏的数据，消耗数据时处理这些不确定性的工作量非常大。

## 一个简单的例子

让我展示一个非常简单的例子，我们如何使用关系模型和约束的组合来限制不确定性。

我们想为 sith 创建一个名称生成器，需要一个表来存储 sith 可能获得的名称。我们还希望有可能定义一个特定的标题作为默认标题。

```
create table sith_title (
id int identity(1,1) primary key,
title nvarchar(100),
is_default bit default 0
);

insert into sith_title ( title, is_default ) values ( 'Acolyte', 0);
insert into sith_title ( title, is_default ) values ( 'Sith', 1 );
insert into sith_title ( title, is_default ) values ( 'Sith Lord', 0 );
insert into sith_title ( title, is_default ) values ( 'Darth', 1 );

select title from sith_title where is_default = 1; 
```

Enter fullscreen mode Exit fullscreen mode

[SQLFiddle](http://www.sqlfiddle.com/#!18/7f22b/1)

由于我们不能确定我们将只得到一个默认条目，我们将不得不处理每个需要默认标题信息的功能中多个默认值的可能性。

在这种情况下，有几种解决方案来限制不确定性，包括触发器，但一个非常简单的方案只是使用关系模型和一个唯一的约束:

```
create table sith_title (
  id int identity(1,1) primary key,
  title nvarchar(100)
 );

create table sith_title_default (
  id decimal(1,0) not null primary key default 1,
  fk_sith_title integer not null,
  constraint fk_sith_title foreign key ( fk_sith_title ) references sith_title ( id ),
  constraint chk_id check ( id = 1 )
 );

insert into sith_title ( title ) values ( 'Acolyte');
insert into sith_title ( title ) values ( 'Sith' );
insert into sith_title ( title ) values ( 'Sith Lord' );
insert into sith_title ( title ) values ( 'Darth' );

insert into sith_title_default ( fk_sith_title )
  select id from sith_title where title = 'Darth';

select title from sith_title where id = (select fk_sith_title from sith_title_default);

insert into sith_title_default ( fk_sith_title )
  select id from sith_title where title = 'Sith'; 
```

Enter fullscreen mode Exit fullscreen mode

[SQLFiddle](http://www.sqlfiddle.com/#!18/6e00f/7)

仍然存在得不到默认值的不确定性，但是我们成功地消除了获得多个默认值的不确定性，因此可以跳过消费函数中的处理。

## 自动自检

当然,“通过测试”也是关于自动化自测的主题(包括单元测试、集成测试、回归测试以及所有其他类型的测试)。

我详细地写过这个话题，我确信在大多数情况下，在你的软件中包含自动化测试对你的项目非常有益。

但是我们必须记住，大多数自动化的自测(特别是如果它只在 QA 环境中而不是在生产中完成的话)只是检查我们所知道的东西的一种形式。

它不能取代探索性测试，当发布新功能时，仅仅依靠你的单元测试可能会过于自信。如果软件是由人们使用的，并且是为了解决人们的问题，那么“测试”在某些时候应该包括他们。

## 更多测试

什么？我们会被期望覆盖更多的测试吗？

我认为有一大堆事情我们还没有解决，但在编写软件时值得考虑。

这份(非详尽的)清单并不意味着是一种负担，而是为了拓宽我们的视野:

*   安全性(SQL 注入、敏感数据、加密)
*   性能(虽然可能存在过度调优的缺陷，但良好的性能是首要要求)
*   可用性(功能可以理解吗？好用吗？为了谁？)
*   对多用户情况的影响(其他用户将如何受到影响，例如由于锁定？)
*   隐私保护(我真的需要来记录吗？什么时候会被删除？)
*   可扩展性(这在 100 倍的数据上表现如何？)
*   监控(我如何注意到它没有按预期工作？)
*   安全(此功能中的错误会伤害人吗？如何避免？)
*   并发性(如果两个用户同时使用会怎么样？)
*   如果数据库在运行过程中出现故障，会发生什么情况？

这些事情中的每一件都可以变成必要的需求，因此是我们的软件必须通过的测试。

这也是为什么我认为纯单元测试和 TDD 不足以回答 Beck 的简单设计规则的原因。它可以是其中的一部分，但是为了确定哪些测试是必要的，我们需要对问题领域、我们希望用我们的软件帮助的人以及我们自己的环境、可能性和情况有深入的了解。

# 一个富有同情心的结论

意识到“通过测试”可能不仅仅意味着为一个函数编写一个快乐路径的单元测试，这可能是压倒性的，甚至是令人沮丧的。要考虑的事情太多了，有时甚至相互矛盾。也许这整件事**是**神秘的知识，只有我们行业中最有经验的人才知道？

在我看来，肯特·贝克的设计规则是一种工具。在许多情况下，了解它们并考虑它们是非常有益的。但它们不是唯一有效的选择，也不是你应该盲目追随的宗教。

好的软件设计取决于。这取决于问题，取决于可用的资源，取决于参与的人员，取决于项目的范围和目标。

这也取决于开发者的经验。关于公司文化。已经存在的软件的质量。

[![sarahmei_sw_design](../Images/904da40d194eb2c4fa2b3b321551f984.png)T2】](https://twitter.com/sarahmei/status/999799423453487104)

我非常喜欢这句话，因为它很实用，没有我们在科技行业经常看到的那种神秘的精英主义态度。

“通过测试”可以导致更成功的项目，它可以帮助编写更好的软件和创造更好的软件设计。它可以帮助减少相关人员的痛苦，无论是用户、开发人员、测试人员还是支持团队。但是如果它变成教条，开始造成痛苦，而不是减少痛苦，那就有问题了，应该进行调查。也许它不是这项工作的合适工具。

伟大的软件设计，首先拥抱[慈悲的代码](https://medium.com/compassionate-coding/what-does-compassion-have-to-do-with-coding-f65b6922a6ff)。

[![Compassionate code minimizes suffering for the people writing it, reading it, using it, and even being indirectly affected by it.](../Images/98b0827e5744c752c5be85908b7bcd67.png)T2】](https://twitter.com/aprilwensel/status/1004008046840827904?ref_src=twsrc%5Etfw)

我会很高兴地一步步走向那个目标。
# 测试心理学

> 原文：<https://dev.to/franiglesias/psicologa-del-testing-5fkp>

我与测试的第一次接触，准确地说，与测试概念本身，至少是一个顿悟。

一开始，我对软件测试的概念和必要性有了相当模糊的认识，幸运的是，随着时间的推移，我一直在开发和完善软件。我今天还在努力改进它。

我也很难进入测试技术。当时 PHP 世界的参考文献很少，也不是对如何编写测试的教学兴趣很大，更不用说良好的测试了。我所有的文件都是提供‘t0’simple test’的，JUunit 家族的一个框架，我不知道是否还有人会记得。

我不告诉你遇到测试-第一和测试驱动型开发方法给我带来的精神冲击。所以在我开始写最简单的测试之前我不认为我需要准备很多东西。在那个时候，一个‘不是’是一个错误，不是我下一个任务的指示。

今天，几年后的今天，我在没有开始测试的情况下编写软件遇到了一个困难。使用它们，我可以通过编写代码或使用安全网络进行修改和重新设计来定义我的目标。作为一个程序员，我的生活肯定比测试更好。

## 测试费用是多少？

从技术上讲，做测试是一件相当简单的事。测试不过是运行一个软件单元并告诉我们返回的值是否与预定值匹配，或者它是否产生了我们预期的效果的一个小程序。

归根结底，一个测试是这样的:

```
$result = // exec some software unit

if ($expected === $result) {
    echo 'OK: the software unit works as expected';
} else {
    echo 'Something is wrong!'
} 
```

Enter fullscreen mode Exit fullscreen mode

当然，为了专业地工作，我们需要更强大的工具和框架，我们在定义什么是软件单元以及确定我们所理解的预期结果方面面临着挑战。

但我们不会在这里讨论这些问题。

我们的目标是提请注意一些我们可以界定为心理方面的问题，这些问题有助于解释为什么测试做法没有如预期的那样广泛。

## 测试的概念和测试的必要性

我们知道软件工作吗？只要看着它工作。测试的第一个问题是，我们看到刚刚编写的软件工作正常。事实上，我们经常谈论同样的手动测试:让我们看看我们编写的代码是否按我们希望的方式运行，如果是的话，我们认为它已经完成。否则，我们将尝试了解失败的原因，并尝试纠正错误，重新开始循环。

这是第一个障碍之一:如果我们看到代码起作用了:∞创建测试要花多少时间和精力才能说出同样的话？

以下是一些原因:

1.  一个测试是一个“T0”的正式定义我们所理解的软件的正常运行，在这个定义中，不同的利益相关者可能会同意。
2.  是**可复制**:测试将给出在各种环境下运行的相同结果，这并不取决于我们是否注意到或者是否记得它必须给出的结果。
3.  是**可重复**:我们可以反复试验多少次，这样我们就可以对代码进行修改，确保它继续产生同样的结果。
4.  是**自动化**:我们可以安排在需要的任何时间运行测试，以及我们拥有的所有其他测试。

也就是说，如果没有测试的支持，我可以就我的代码如何工作提出的说法就没有那么重要。测试是衡量软件是否正常运行的一种尺度。

另一个问题是，我们是否用给定的测试来正确地测量。但确切地说，有一个测试使我们能够评估该测试是否衡量了我们希望它衡量的东西。

## 我们对自己的代码感到依恋

我们倾向于对我们的代码感兴趣。也许很丑，但那是我们的。事实上，我们从来没有见过他丑陋，我们觉得他是一只白色漂亮的独角兽。

以更技术性、更少戏剧性的方式说:我们都有一定的偏向于我们自己的守则，所以测试它可能会花费我们的努力。不是因为它可能带来的技术困难，也不是因为我们将在后面讨论的问题，而是因为它使我们对我们自己的工作持批评态度。

我要特别指出影响测试我们制定的守则的心理困难的下列因素:

1.  **任务完成**:当我们使一个代码工作时，我们有完成任务的感觉，所以测试阶段变得格外困难。我们的思想已经进入如下模式
2.  **独特的解决办法**:我们大多数人都经历过一种教育制度，这种制度在我们的大脑中灌输了只有正确的解决问题办法的思想。一种躁狂的文化，在这种文化中，事物要么是好的，要么是坏的，评价被认为是一种危险而不是一种诊断形式(看看是否在罕见的情况下会失败)。

但是，摆脱这种对代码本身的主观看法？也许最好的方法是采用 TDD 和 BDD 等方法*首先测试*。

通过在代码之前进行测试，我们可以:

*   让测试告诉我们下一步是什么:在所有测试都通过之前，任务不会结束。
*   由于我们没有预先编写的代码，因此我们对某个设计没有偏见，而是根据测试要求对其进行定义。
*   我们可以随时告诉您代码的状态，因为我们已将规格设计为测试，并知道哪些规格已得到满足，哪些尚未得到满足。

## 测试的技术难点

众所周知，有许多设计使得测试代码特别困难。特别是在具有高度耦合或全局依存关系的情况下。

这种困难可能会导致我们避开试验阶段，或者只限于对 *happyu path* 的检验。

虽然有处理这些情况的具体技术，但理想的做法是*试验优先*。为了满足测试要求，我们的设计从一开始就考虑到了这一点，问题情况(坞站、全球运行状况依赖项等)会立即显现出来，迫使我们采用能够减少或避免这些问题的解决方案。

## 不测试的压力

将产品或功能推出市场的需要或匆忙可能会给组织带来压力，迫使其尽快交付。因此，任何无助于实现这一目标的东西都往往被忽视，而测试往往是试图轻而易举地放弃的第一件事。

回到上一点来看，完成任务的感觉在这里是决定性的:∞产品工作，应该是什么

答案是另一个问题:∞你能说产品在没有测试的情况下工作吗？

您通常具有以下经验:花费时间开发代码、交付代码，并且必须花费相同或更多时间来修复产品交付后出现的错误。从而使**成品**的定义完全受到质疑:∞如果我们要纠正在许多常见使用情形下妨碍其工作的错误，说一个产品是成品？

我们花在纠正错误上的时间本可以通过适当的测试来预防错误，从而指导发展。不仅如此，错误还可能造成收入损失、负面宣传等后果，这些后果是可以衡量的，而且很可能比试图确保良好的测试复盖率要高。

在流行的科学观中，通常认为一个成功的实验证明了一个理论的正确性。但事实并非如此，实验的目标恰恰相反。就是所谓的**破产**。

按照谬误的思想，一个成功的实验并不证明它所依据的理论是真实的，而是在它被证明的程度上并不虚假。这种观点的转变是至关重要的:实验的设计是为了驳斥这种理论，这样，如果它能奏效，它就能为我们提供信息，我们就能暂时接受它。

软件测试也会发生类似的情况。给定的测试可能会通过，但这并不能保证软件工作正常，因为在某些情况下可能不会。测试应检查软件故障，即测试可能会影响其功能的情况。这些案例越多，我们就越能以测试的形式表示软件的工作原理。

*快乐路径*的测试，也就是只锻炼我们代码完美流动的测试，并不能保证它的运行，尽管它确实帮助我们提供了它应该如何行为的正式表示。

## 责任与测试

我们的世界越来越依赖于软件。∞你是否曾经停止思考过你的代码按预期工作或不按预期工作的后果？

如果建筑师或工程师设计的结构计算错误且崩溃，则他们负有民事责任。想想这会造成多大的经济损失。但是，如果那次倒塌造成伤害或死亡呢？

你在做什么软件产品？如今，软件控制着各种设备和各种服务。举几个例子:

*   一个错误可能会导致一个用户在为永远不会得到的服务付费时损失一笔钱:∞对那个人来说，大是损失吗？。
*   另一个错误可能导致医院对病人的错误诊断，从而导致不适当的治疗。
*   另一个错误可能会使一个人无法前往参加工作面试，失去一个可能不会再出现的就业机会。

软件故障的后果不仅仅是给个人或公司造成不便或经济损失，我们无法预测。

上下文至关重要，事实上，为网上超级市场编写软件与为航空导航系统或医疗诊断辅助软件编写软件并不相同。在这种背景下，我们可以预见一些可能的后果，并采取适当行动。每种情况都对我们的守则的可靠性和准确性有不同的要求。但这并不能免除我们尽最大努力的责任，测试是实现这一目标的一种手段。

测试并不能保证软件没有缺陷，这是事实，但它表明我们正在采取措施以最佳方式创建软件。
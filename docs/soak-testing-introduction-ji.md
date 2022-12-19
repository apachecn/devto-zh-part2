# 浸泡测试游戏攻略

> 原文：<https://dev.to/katalon/soak-testing-introduction-ji>

[![Soak Testing](../Images/6232f1be812484d30f7c0c3200127621.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--rycI7QKh--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://d1h3p5fzmizjvp.cloudfront.net/wp-content/uploads/2018/08/13173431/soak-testing.png)

## 简介

如果您计划在运行期间实现或保持系统的最高性能，您可能需要进行一些性能测试，以验证系统在开发周期的最后阶段的稳定性和负载。这种测试称为浸泡测试，它可以帮助您在特定平台上发布产品之前，立即发现与性能相关的问题，例如内存泄漏或资源泄漏。

## 什么是浸泡测试？

浸泡测试(也称为耐久性测试、容量测试或寿命测试)包括测试系统，通过请求系统上的设计负载来检测与性能相关的问题，如稳定性和响应时间。然后对系统进行评估，看它是否能在长时间的大负载下运行良好，从而测量它的反应并分析它在持续使用下的行为。浸泡测试是一种负载测试。

如今有无数的浸泡测试工具，如 LoadStorm、LoadRunner、LoadUI、OpenSTA、Apache JMeter、Appvance 和 WebLoad。

此外，还有一些保证你的系统在正常情况下正常工作的支持工具，如[卡塔龙工作室](https://www.katalon.com)、[硒](https://www.seleniumhq.org/)、[机器人框架](//robotframework.org/)。

## 浸泡测试示例

理想情况下，浸泡测试应该运行尽可能长的时间，尽管它将由您的系统来决定测试的持续时间。以下是可以考虑浸泡测试的一些例子:

*   当一家银行宣布将关闭时，其系统预计将在银行关闭期间处理大量交易。这种情况很少发生，也很意外，但是你的系统必须处理这种不太可能发生的情况。
*   一个系统需要经受住没有待命人员的时期。通常，这种情况会在员工周末不工作时发生，因此浸泡测试将证明系统能够在比周末更长的时间内不间断运行。
*   您的系统需要在 1 小时内处理 1000 笔交易。您可能不仅需要测试这种能力，还需要超出这一要求:在半小时内测试 1000 个事务，或者在 1 小时内测试 2000 个事务。

## 浸泡测试的几点考虑

*   浸泡测试的持续时间通常由系统的可用性决定。
*   每个应用程序都必须不间断地运行。
*   每个系统通常都有一个频繁的维护窗口时间；该时间将是决定浸泡试验范围的关键因素。

## 为什么要进行浸泡试验？

浸泡测试主要用于识别和优化潜在的问题，如内存泄漏、资源泄漏或随时间推移可能发生的降级，以避免性能受损或系统错误。虽然压力测试将帮助开发团队测试系统的极限，但是浸泡测试会在持续使用一段时间后使系统达到极限。换句话说，浸泡测试允许团队模拟真实世界的使用，在这种情况下，用户将不断地需要访问系统。

## 浸泡测试带来的优势

*   它保证了应用程序的适用性。
*   它检测其他性能测试无法发现的错误。
*   它发现在高持续负载下可能发生的性能下降，并帮助修复这些问题，使应用程序更加健壮。
*   它显示了系统运行的可持续性。
*   测试结果可用于验证或改善客户的基础设施需求。

## 浸泡测试的挑战？

*   该测试是一个耗时的过程，并且在时间限制非常严格的项目上进行是不方便的。
*   您需要将自动化工具与技术专家结合使用，因为浸泡测试会运行很长一段时间，并且会消耗大量数据。
*   通常很难确定有多少测试值得应用。
*   如果测试环境没有正确地与实际生产环境分离，浸泡测试发现的错误可能会对整个工作系统产生负面影响，导致永久的数据丢失或数据损坏。

## 什么时候做浸泡测试？

在特定平台上向客户发布系统之前，它必须在更高或类似的流量级别上成功地进行一系列负载测试。然后执行浸泡测试。浸泡测试将帮助您了解系统如何在连续可用性期间运行。如果在测试过程中出现任何问题，如内存泄漏或内存损坏，应立即报告。

由于这个过程可能需要一天的时间，浸泡测试应该在周末进行，尽管这也完全取决于测试环境的限制。

浸泡测试现在是任何团队为了成功的部署都必须严格遵守的最重要的需求之一。

## 浸泡测试策略

在执行浸泡测试之前，您需要鸟瞰系统并确定:

*   测试环境:
    找出执行浸泡测试的硬件、软件、数据库和操作系统。

*   测试场景:
    因为浸泡测试是一个广泛的过程，所以在执行任何测试之前，设计、检查和最终确定测试场景是很重要的。在这里，开发团队还需要确定系统的负载有多重。

测试评估:
浸泡测试的持续时间取决于系统的范围。它还依赖于开发团队和客户的参与，实际的生产使用，等等。

*   风险分析:考虑一些问题，例如:浸泡测试如何在使用过程中保持一致？有没有尚未被检测到的 bug？是否有任何外部干扰会导致系统停机？

## 浸泡测试检测到的常见问题有哪些？

*   内存分配(最终导致内存危机或舍入失败的内存泄漏只会随着时间的推移而显示出来)。
*   数据库资源使用情况(在某些情况下关闭数据库游标时出错，最终会导致整个系统停止运行)。
*   它还会导致性能下降，也就是说，要确保在一段时间后的响应时间与测试开始时一样好。
*   在某些情况下关闭多层系统各层之间的连接时出现错误，可能会阻塞其部分或全部模块。
*   随着测试时间的延长，内部数据结构的组织性降低，某些任务的响应时间逐渐缩短。

在进行任何浸泡测试之前，确保您的系统在正常条件下正常工作是非常重要的。 **Katalon Studio** 为软件测试提供了一个[的简单解决方案，帮助开发周期平稳运行，保证成功部署。](https://www.katalon.com)

**来源:[什么是浸泡测试？](https://www.katalon.com/resources-center/blog/soak-testing/)**
**更多:[关于自动化测试的真知灼见](https://www.katalon.com/resources-center/blog/)**
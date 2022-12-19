# 如何编写 React 组件的测试？

> 原文：<https://dev.to/squgeim/how-do-you-write-tests-for-react-components-20nl>

我尝试了很多策略来解决这个问题。我对大多数简单的组件进行了快照测试；但是，当涉及到 redux 和其他库时，即使是对一个小组件进行快照测试，结果也是工作量太大；除非你浅薄的渲染。然后，您从测试中完成的唯一事情是组件是否呈现。

编写单元测试的最好方法是先编写测试，这样你只需要考虑不同条件下你需要什么样的输出，而不用担心实现。在测试组件功能的情况下，我看到了模拟按钮点击的测试。你在组件完成后编写测试吗？这难道不会增加为所有情况编写测试的难度吗(您的测试往往会因实现而有所偏差)？还是像编写组件一样编写它们？

你为 UI 编写测试的方法是什么？我觉得我错过了一些重要的东西。
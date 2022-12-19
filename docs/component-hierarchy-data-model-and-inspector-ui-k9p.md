# 组件层次结构数据模型和检查器 UI

> 原文：<https://dev.to/progrium/component-hierarchy-data-model-and-inspector-ui-k9p>

继续我的 TreeView 原型，我一直在试验 TreeView 背后的节点的实际数据模型。之前我们有一个 TreeNode，但这实际上是一个更复杂的节点的表示，它有自己的树结构。因此，我实现了该数据模型，并将 UI 中的更改与该数据模型的更改绑定在一起，因为它随后创建了 TreeView 组件使用的 TreeNode 表示。

我还必须确保这是一个可序列化的数据结构。这导致了一些迭代，但我现在非常简单。我几乎有了一个单独的结构来模拟数据如何被序列化，但是这样我就有了一个节点的三个不同视图。

我还带来了一些组件。首先作为数据模型的一部分，并让它们正确序列化。这很棘手，因为一个组件几乎可以是任何结构，我们希望将其反序列化为正确的类型。因此，我们必须将它包装在一个具有类型名称的数据结构中，我们可以将它放入我们的某种组件工厂中，以获得一个新的实例并将其解组。我还第一次使用了`MarshalJSON`和`UnmarshalJSON`接口，让我部分解组一个略有不同的表示来获得类型名，然后在创建一个组件实例后解组其余的。

然后，我准备重新创建原始原型的属性检查器。我想用 UI 组件重新创建它，而不是包装以前的 jQuery 库。通过这种方式，我可以更好地了解 UI 框架。我遇到了一些我能够修复或解决的问题，但是它正在列出节点的字段名和它拥有的任何组件。

能够使用我的 WASM UI 框架和大部分正常工作是令人兴奋的。

[https://www.youtube.com/embed/0yFRQGgIRec](https://www.youtube.com/embed/0yFRQGgIRec)
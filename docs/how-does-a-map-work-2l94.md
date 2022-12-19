# 地图是如何工作的？

> 原文：<https://dev.to/jvanbruegge/how-does-a-map-work-2l94>

有时候，作为开发人员，您希望存储键值对。例如，您可能希望通过用户名访问用户对象。最适合的数据结构是一个**地图**。它允许我们通过它在`O(1)`中的唯一键获得一个值。如果你不熟悉 Big-O 记谱法，可以看看我的文章。

就拿你能想到的最简单的图来说吧:一个数组！它存储键-值对，但是键仅限于自然整数。数组中的随机存取是`O(1)`。但是为什么呢？

在内存中，数组是一个连续的内存块。此外，您还必须知道数组在内存中的起始位置，以及各个元素有多大。要访问一个随机元素，只需取索引，用它乘以元素大小(假设元素大小一致)，然后加上数组的起始地址:

```
memory_location_to_fetch = index * size_of_single_element + start_of_array 
```

# 散列法

好吧，但是如果我们想用字符串来索引我们的元素呢？这里我们将使用一种叫做*散列*的技术。一个散列函数接受一个**任意**长度的输入，并产生一个**固定**长度的确定性输出。这通常由模运算符来完成。

```
hash(x) = f(x) ℅ size_of_map 
```

`f(x)`是一些依赖于实现的任意函数。最简单的函数是*身份* : `f(x) = x`。

那么字符串作为键呢？还是物件？

# 一切都是整数

如果我们回到计算机内存，一切都是以二进制存储的。但是没有什么能阻止你*将*二进制解释为普通整数。让我们用一个简单的字符串作为例子。c-string 只是一个连续内存块中的 ASCII 字符，以零字节为后缀。要将(二进制)数转换成 ASCII 码，使用 [ASCII 码表](http://www.asciitable.com/)。例如，我们将把字符串`Hello`转换成它的数字表示(这里是十六进制，因为转换成二进制比十进制更容易):

```
 H     e     l     l     o     \0
0x48  0x65  0x6C  0x6C  0x6F  0x00 
```

我们现在可以简单地将这 6 个字节解释为一个数字，并且我们可以使用这个数字作为哈希函数的输入。

# 哈希冲突

您可能已经问过自己，如果两个不同的值被散列得到相同的结果，会发生什么？例如，我们有一张大小为`10`的地图，放入`0`、`10`、`20`等等？

为此，我们可以实施回避策略:

*   线性散列法:如果某个位置已经被占用，则按固定的数量(通常为 1)移动新的值
*   双重散列:如果 sport 被替换，只需再次散列散列并将我们的元素放在那里
*   使用链表作为数组元素并附加碰撞。这实际上给了我们充满具有相同散列值的对象的“桶”。

# 汇集一切

我们现在将实现一个首先只适用于整数的映射。对于这里的例子，我将使用 Typescript。

正如我们已经看到的，我们可以将每种类型表示为整数，所以我们现在只关心整数。

首先，我们实际存储在地图中的是:

```
class OurMap<Value> {
    private array: [number, Value][];

    constructor(size: number) {
        this.array = new Array(size);
    }
} 
```

我们只是定义了一个固定长度的数组来存储我们的键值对。

现在我们添加一个`insert`方法:

```
class OurMap<Value> {
    private array: [number, Value][];

    constructor(size: number) {
        this.array = new Array(size);
    }

    public insert(key: number, value: Value) {
        const origIndex = this.hash(key);
        let index = origIndex;
        while(this.array[index] !== undefined
          && this.array[index][0] !== key) {
            index = (index + 1) % this.array.length;
            if(index === origIndex) {
                throw new Error('Map is already full');
            }
        }
        this.array[index] = [key, value];
    }
} 
```

你能看出我们使用了什么防撞策略吗？如果你说线性散列，你是对的！如果我们的位置已经有人了，我们就向右走一个。

`get`方法与 insert 方法的工作方式完全相同，它只是不检查`undefined`而是检查你传入的键。

删除也是类似的，但是我们还必须检查右边的元素。如果有一个元素，它可能是通过我们的线性散列得到的，所以如果原始元素丢失了,`get`将不会试图查看右边。我们必须将这些元素移回左侧。这当然会导致进一步的修正。

# 奖励回合:套

你可能也偶然发现了**集**。事实证明，你可以用一个映射来实现一个集合。在旧版本的谷歌浏览器中，你可以在开发工具中看到这一点。在这里，集合具有与映射相同的属性(键和值，而不仅仅是值)。

让我们通过简单地使用我们的键作为值来复制这种方法。

```
class OurSet {
    private map: OurMap<number>;

    constructor(size: number) {
        this.map = new OurMap<number>(size);
    }

    public insert(value: number) {
        this.map.insert(value, value);
    }
} 
```

这是可行的，因为使用相同的密钥将总是导致相同的存储位置。因此，如果已经有了密钥，您可以覆盖它，这不会改变任何事情。如果没有条目，您可以知道这个键在集合中还不存在。

# 透视事物

数据结构都是关于权衡和用例的。那么我们的地图在哪里呢？

地图和数组一样，有`O(1)`插入，随机访问和删除。不过这取决于地图的实现。两者都必须预先分配一个固定的大小。如果你需要一个动态增长的数据结构，你应该使用链表。对于插入和顺序访问，它也是`O(1)`，但是对于删除和随机访问，它是`O(n)`。

如果只想存储多个元素以便于迭代，可以使用数组。如果需要键值查找，请使用映射。您可以使用数组，但是映射处理散列冲突，而数组只会覆盖旧值。

# 结论

我希望你在这篇文章中学到了一些新的东西。这是我的数据结构系列的第二部分，你可以在这里找到第一部分(关于 Big-O 符号)。欢迎分享任何反馈。
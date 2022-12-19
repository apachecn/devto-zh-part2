# 阅读障碍如何帮助我成为一名程序员

> 原文：<https://dev.to/rapidnerd/how-dyslexia-helped-me-become-a-programmer-136d>

从小我就知道我的阅读和拼写有问题，但从来不知道具体是什么问题。直到第八年(在美国读大三)，我才接受了测试，那时他们告诉我，我有一种令人讨厌的东西，叫做诵读困难症。

在很小的时候，我就知道我想进入的职业道路是基于技术的，我喜欢做硬件，但对写代码更感兴趣。但是诵读困难症发作了，我记东西不容易，拼写不正确，最糟糕的是我把很多东西搞混了。在学习了 batch 的基础知识之后，我转而学习 Java，这是它开始对我产生严重影响的地方。我发现学习语法很好，我可以很容易地记住它。然而，当谈到记忆定义、数据类型的不同用途、如何编写干净的代码、标准的库用法时，它左耳进右耳出。

因为当时对我来说是暑假，我给自己设定了目标，我想变得足够流利，我可以制作基本的像素艺术游戏，没有什么太疯狂的，只要它能工作，不会用我糟糕的代码库点燃我的 CPU。但我发现，即使在遵循教程并多次做同样的事情试图记住它之后，它仍然不会坚持。在
之前，我至少写了 12 遍这个脚本

```
 public void keyPressed(KeyEvent e) {
        int key = e.getKeyCode();
        for (int i = 0; i < handler.object.size(); i++) {
            GameObject tempObject = handler.object.get(i);
            if (tempObject.getId() == ID.Player) {
                if (key == KeyEvent.VK_W) {
                    tempObject.setVelY(-5);
                    keyDown[0] = true;
                }
                if (key == KeyEvent.VK_S) {
                    tempObject.setVelY(5);
                    keyDown[1] = true;
                }
                if (key == KeyEvent.VK_D) {
                    tempObject.setVelY(5);
                    keyDown[2] = true;
                }
                if (key == KeyEvent.VK_A) {
                    tempObject.setVelY(-5);
                    keyDown[3] = true;
                }

            }
        }
        if (key == KeyEvent.VK_ESCAPE) System.exit(1);
    }
/***
* a basic event that listenes for a key event, when it is pressed it will
* move the player around to the coordinates depending on the press, also 
* assigns a boolean value for some reason that I can't remember.
***/ 
```

Enter fullscreen mode Exit fullscreen mode

印象不深刻，但对我来说，这是一个学习曲线。我在自己的游戏教程中使用了它，你会认为写了这么多之后，它的用法和概念会留在我的脑海中。没有。什么都不记得了。就在那时，我回到了帮助部门，问我学校的人这是否正常。他们说我有阅读障碍，记忆东西有问题是很常见的，尤其是那些复杂的东西。

这件事对我打击很大，让我心情很差，几乎让我放弃了。我一直在努力记住并从编程中学到很多东西，但因为一个条件，我知道坚持下去会很痛苦。在我放弃的两个月里，我看着我的朋友们在他们的学习经历中取得成功，做他们喜欢的任何东西，而我只是坐在那里希望我脑子里的东西会消失。

直到我的朋友杰克找到我，问我最近在做什么，我才告诉他我已经放弃了，因为我正在忘记事情，并告诉他我有什么条件。大约一个小时的谈话后，他告诉我，他和我一样，放弃不是办法。那周晚些时候，我去了他家，被我所看到的震惊了。他的桌子上到处都是一堆笔记，粘在他的显示器上，他的塔上，甚至他的椅子上。我想有一次他的猫在咀嚼它们。但是他有一种格式，一种他用来记住他需要的重要信息的格式。带回家一个例子，我试了一下，用上面的代码，我用格式把它写在指定的方框里。

两天之内，我就通过格式、颜色编码、物体和数字的分配记住了代码，这给了我一个如何记住所有重要信息的好主意。虽然它不能用于每一段代码，但我终于有了一种记忆的方式，这真是太好了。

谢谢你，杰克！！！

几个月过去了，我发现这种形式对我来说就像一个梦，我记住了比我能记住的更多的东西，并且在学习曲线上做随机的垃圾时获得了巨大的乐趣。我有一个笔记本，当你跳过它时，它看起来像一道彩虹。

现在我面临一个新问题。数学！

问问我认识的任何人，我的数学很糟糕，我可以做基本的数学，但当涉及到代数、三角学和微积分时(尽管在英国我们没有学过这些)，我会陷入难以置信的困境。在学校与系里的人交谈时，他们教了我一个类似记忆的技巧。通过为等式的每个方面分配不同的颜色，并将两种颜色混合在一起，得到输出。例如，如果我用绿色表示第一个数字，然后用红色表示第二个数字，那么输出就是黄色。我发现用简单的记忆技巧来记住我需要记住的公式、方程和一般信息对我和其他有阅读障碍的程序员都有很大的好处。不仅仅是颜色、形状，其他实体也有很大的帮助。

### 给那些认为自己有阅读障碍或已经有阅读障碍的人的建议。

1:如果你认为你有，但没有被诊断出来，去检查一下。

多年来，我在正常的学校和社交生活中，一直认为自己有问题，认为自己的精神不正常。从专业人士那里得到正确的诊断无疑让我卸下了一大块重担。

2:有奇怪的记忆方式没关系。

每个人对重要信息的记忆都不一样，有些人把它写下来，有些人不停地说/写，直到永远记在脑子里。有一次，我的一个前同事把它纹在了身上。只要你有记住它的方法，那就是最重要的。

3:这不会让你成为一个糟糕的程序员。

我脑海中闪过的一个想法是，因为一个条件，我永远不会在职业生涯中取得任何成就，而在我找到一个最终让我满意的地方之前，我还有很长的路要走。有阅读障碍可能会在一段时间内破坏我的思维模式，并阻止我走得更远，但我相信它帮助我变得更强大，并在编程世界中对我有很大帮助。

4:如果你在接受某种形式的教育，使用任何提供的资源。

纵观我在教育机构(甚至今天在大学)获得的所有资源，它极大地帮助了我提高工作和教育生活的各个方面，显然每个地方都将是不同的，但给出的技术是一个很大的帮助。大多数时候它是免费的或者被其他人覆盖。

虽然今天阅读障碍、计算障碍和运动障碍仍然是我生活中的主要部分，但我不认为它们是一个问题或障碍，我认为它们是我身上的某种东西，使我变得更强大。

一些关于阅读障碍的帮助和学习资源:
[阅读障碍帮助&支持](http://www.dyslexiahelp.co.uk/)
[阅读障碍基金会](http://www.dyslexia-help.org/)
[NHS 阅读障碍管理](https://www.nhs.uk/conditions/dyslexia/living-with/)
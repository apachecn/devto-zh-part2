# 一只小虫子的故事

> 原文：<https://dev.to/ohffs/story-of-a-little-bug-4ppb>

我们的一个应用程序有一个功能，用户可以切换发送电子邮件通知别人的选项。邮件会延迟 30 分钟，这样用户就可以改变主意(或者意识到他们一开始就做错了)...).一切都好。

不久前，对代码和电子邮件模板做了一个小的改动，所以我们推出了一个新版本。这种推送是通过[部署者](https://deployer.org/)进行的，部署者通过将一个发布目录符号链接到一个“当前”目录来实现“零宕机”,而应用正是从这个“当前”目录提供服务的。默认情况下，它保留了之前的五个版本，因此如果需要，您可以回滚。一切都好。

该应用程序使用一个后台队列来发送这封特定的电子邮件——作业被延迟 30 分钟，在最终发送之前，它会检查切换是否仍处于“是-做那件事”模式。当我们部署上述更改时，我们手动重启了整个队列，以确保它与新代码同步。同样，一切都很好——一切都运行良好。在这一天中，我们又推出了一些小更新。

## 六周后...

我们收到一封来自办公室管理员的邮件，说他们认为电子邮件不会再从系统中发出去了。大约一周前，我们遭遇了一次相当残酷的停电，我的第一个想法是“哦，该死——有什么东西没有正常重启”。尽管[哨兵](https://sentry.io/welcome/)没有发现任何错误，我们的日志监视器也没有发现任何问题。

检查队列状态显示它被标记为“暂停”。我以前遇到过这种情况，两个应用程序共享一个 Redis 实例，他们不知道应该处理哪些作业——毫无疑问，服务器上有另一个应用程序，它指向同一个 Redis 数据库。因此，我们将有问题的应用程序的 db 值提高了一个，并重新启动了队列——现在队列显示为健康的，测试消息显示为 ok。“唷！”我认为——很好的简单解决办法，并在心里记下，最终要确保所有的应用程序都有一个指定的数据库，这样它们就不会冲突。

然后我开始想——等等，另一个应用配置了 Redis 但它实际上并不使用队列。这只是一个默认，我们已经习惯于把它作为“我们可能会在某个时候使用 Redis，包括默认配置”来对待。所以我做了更多的调查...

检查应用程序自己的错误日志没有显示任何有趣的东西。所以我检查了服务器上的系统日志，在我重新启动它们之前，看到了很多来自队列工作器的“无法打开文件/路径/到/释放/65/”消息。那是什么...奇怪。尤其是我们的日志监视器没有发现它。

队列工作器通过 systemd 启动并指向`/path/to/current/`，这样它们在运行时应该使用最新的版本。但是我没有注意到，他们*实际上*看到了符号链接，并将其解析到“真实”目录，因此转到了“/path/to/release/65/”，这是“当前”当时指向的位置。

自从上一次手动“重启整个队列进程”以来，已经推出了五个其他的小更改——每个都应该重启队列工作器，所以*不应该*成为问题。但是，我没有注意到——用于重启队列的命令并没有重启主进程——只是告诉主进程根据它自己对路径的想法重启工作进程*。所以在第五次推送之后，主进程现在指向一个目录，这个目录已经被`deployer`命令删除，因为它是第六老的版本...*

Sentry 没有找到它，因为它永远无法加载足够的代码来注册处理程序。事实还证明，当服务器已经建成时，这个人没有在上面运行 [Puppet](https://puppet.com/) ，所以它没有安装日志转发/监控设置。systemd 进程处理程序认为一切正常，因为主进程继续愉快地运行，因为它已经将所有代码加载到 RAM 中。

## 包装完毕...

所以总的来说，系统已经有将近六个星期没有发出一份电子邮件了。谢天谢地，这是一年中这个特殊功能非常安静的时候，所以只有少数通知没有发出。但这是一个有趣的早晨，追溯错误，为什么所有的监控层都没有注意到，符号链接如何发现我们并拼凑服务器本身的历史。

现在，除了现有的监控之外，我还从前端获取了一些代码，向我们展示了队列最初是“暂停”的，并使用它来完成一个小 cron 任务，即如果一切都不顺利，*会向哨兵发出*警报。*大概是*...；-)
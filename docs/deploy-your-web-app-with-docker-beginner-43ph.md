# 使用 Docker 部署您的 web 应用程序(初学者)

> 原文：<https://dev.to/quangle/deploy-your-web-app-with-docker-beginner-43ph>

在 BeCode 实习期间，我已经能够用 [GitHub pages](https://pages.github.com/) 或 [Heroku](https://www.heroku.com/) 处理所有部署。然后，上周，数据库出现了。

长话短说，我们必须用 mySQL 数据库开发一个基本的客户端注册(所以再见了 Heroku)。在本地，一切都像预期的那样工作，但是——我很肯定你能看到将要发生什么——当我们试图部署时，整个系统崩溃了。

在分享一些如何让你的生活变得更轻松的技巧之前，让我来分享一下出错的原因。

应用程序的细节并不重要，但这里有一点点背景:

*   我们没有预料到部署将需要大量的时间，所以我们直到最后一刻才开始，这使得混乱和恐慌更加严重。
*   我曾在空闲时间摆弄过服务器上的 Docker，但无法让它工作

所以我们选择了一个免费的托管服务，把他们服务器上的所有文件都搬走了，然后什么都没用。

似乎发生的事情是，服务器运行的 PHP 版本与我们用来开发网站的版本不同。如果我们早点做好调查，这本来是可以避免的，但是，嘿，我们从错误中学习。

这让我想到了这篇文章的核心内容:使用 Docker 进行部署。

上面的小故事表明，部署您的站点或应用程序的棘手之处在于，您的主机提供的环境可能与您的开发环境有很大不同。因此，在规划项目时，您需要预测和分配部署时间。

现在，如果你正在阅读这篇文章，并且已经听说过 Docker，你就知道它的发展方向了:使用 Docker 可以通过在你的服务器上复制你的开发环境，让你的生活变得更加简单。

如果你想了解什么是 [Docker](https://www.docker.com/) 以及它是如何工作的，我会让你点击这个链接。让我来分享一下我是如何使用它将我们的站点重新部署到其他地方并为我们节省了一些繁琐的工作:

1.  选择你的主机。我选择了[数字海洋](https://www.digitalocean.com/)，因为这是我信任的人推荐的。尽管这不是免费的。

2.  在服务器上安装 Docker
    原来数字海洋允许你创建已经安装了 Docker 的虚拟机。如果你想手动完成，就找一个 Ubuntu 服务器，按照[这个教程](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)(别忘了安装 docker-compose)。

3.  将你的`docker-compose.yml`导入你的服务器
    这是神奇的部分:如果你使用 Docker 来设置你的开发环境，*你已经有这个文件*。你所需要做的就是把它放在一个存储库(GitHub，BitBucket，无论你喜欢什么)上，然后在你的服务器上克隆它。

4.  创建容器
    转到将包含您的应用程序的文件夹，将`docker-compose.yml`放入其中，然后:

`docker-compose up`

就是这样。差不多吧。此时，您可能需要重新启动服务器才能工作。我不知道为什么，但我不得不这样做。

现在，你需要做的就是在你的服务器上正确的文件夹中克隆你的应用程序库，你的应用程序将会像在本地运行一样运行，因为它将会在完全相同的环境中运行。

那会节省你一些时间。
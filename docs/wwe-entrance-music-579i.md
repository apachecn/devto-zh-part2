# WWE 入场音乐

> 原文：<https://dev.to/mohanarpit/wwe-entrance-music-579i>

每个人都应该有一首进行曲来宣告他们的到来。我认为这是给 WWE 摔跤手的最大额外津贴。为了复制这种行为，我用 Golang 写了一个有趣的小程序，你可以在这里查看。

### 基本设计

用户的手机总是会在到达门口之前连接到您的家庭/办公室 Wifi 网络。我试图在构建应用程序时利用这一事实。工作流程如下:

*   持续轮询 Wifi 网络以检查最近连接的任何新设备。
*   如果发现新设备，将其 mac 地址与预先配置的设备列表进行比较。
*   如果找到匹配，在扬声器上播放预先配置的声音文件。

这个程序可以在一个树莓派或你拥有的废弃笔记本电脑上运行。它只需要一直在线并连接到 Wifi 和扬声器。

### 挑战

我面临的最大障碍之一是可靠地获取本地网络上连接的设备列表。虽然有许多工具，如`nmap`和`arp-scan`，但它们并不可靠。例如，`nmap`(默认情况下)依靠 PING 扫描来定位设备。另一方面，大多数设备不能可靠地响应 ICMP 请求。

事实上，大多数设备认为这种网络扫描行为是恶意的，默认设置是为了保护用户免受这种行为的影响。iOS 很难被可靠地检测到。有变通办法，但我希望不要使代码太复杂。在一个令人沮丧的时刻，我甚至考虑抓取路由器管理界面来获得连接的客户端列表。

我有一台 DLink DIR-800 路由器，它不支持 DD-WRT 固件。我听说 DD-WRT 有能力通过一些队列发布这些信息，但不幸的是，这不是我的选择。

### 解

如果来自我机器的`arp-scan`不可靠，如果我在路由器上执行它会有什么不同吗？幸运的是，我的路由器支持 Telnet 连接。我通过 telnet 登录到我的路由器，令人惊讶的是它打开了一个完整的外壳！太不可思议了。

```
$ telnet 192.168.0.1 23
Trying 192.168.0.1...
Connected to ralink.dlink.com.
Escape character is '^]'.

ralink login: admin
Password: 

BusyBox v1.12.1 (2014-12-11 15:09:57 CST) built-in shell (ash)
Enter 'help' for a list of built-in commands.

# echo $SHELL
/bin/sh 
```

Enter fullscreen mode Exit fullscreen mode

很好，现在我需要做的就是从路由器执行一个`arp-scan`并解析结果。

在 Linux 系统上，`arp-scan`从文件`/proc/net/arp`中读取值。因此，我没有使用命令，而是直接读取该文件并解析其内容。

```
# cat /proc/net/arp 
IP address       HW type Flags       HW address            Mask     Device
192.168.0.103    0x1         0x2         11:11:11:11:11:11     *        br0
192.168.0.102    0x1         0x2         22:22:22:22:22:22     *        br0
192.168.0.104    0x1         0x0         44:44:44:44:44:44     *        br0 
```

Enter fullscreen mode Exit fullscreen mode

一个 **0x2** 标志表示设备已连接，而 **0x0** 表示设备未连接。

注意:ARP 文件确实需要一点时间来反映任何连接的断开。某些设备上的 ARP 缓存甚至可能是 4 小时。您的里程可能会有所不同。但是新的联系很快在这里得到了反映。

### 最终结果

我把它们都放在一个小而有趣的实用程序中(源代码在这里[可以找到](https://github.com/mohanarpit/wwe-entrance))。我有一台旧的索尼 Vaio 笔记本电脑放在周围，我掸了掸灰尘，拿出来运行这段代码。现在，每当我走进房间/办公室，我最喜欢的歌曲就会出现在我面前！

方便的副作用:在配置了几个朋友的电话后，我知道谁在拜访我，甚至在他们按门铃之前。

### 其他应用

您还可以使用该实用程序为您办公室的同事添加一些个性化内容。对于小公司和初创公司来说，这可能是一个令人讨厌的区别点。

### 未来的工作

由于，我家里只有 1 台路由器，无法用其他型号和厂家测试这个程序。如果你觉得这个项目很有趣，我很想听听你如何通过 CLI 连接到你的 Wifi 路由器。我会相应地对项目进行改进。
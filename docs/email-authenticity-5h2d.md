# 电子邮件真实性

> 原文：<https://dev.to/orliesaurus/email-authenticity-5h2d>

[![Email Authenticity](../Images/01f9b6b6bc9f7532b26b78d52fca54c0.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--KND4mPSV--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://i.imgur.com/rkY895L.png)

## 什么是邮件真实性？

你有多少次收到来自银行和你使用的服务的电子邮件，有拼写错误或要求你的密码。是的，这就是网络钓鱼。

你意识到这封邮件有些可疑。很有可能有人使用易受攻击的 SMTP 服务器(发送电子邮件的服务器)来假冒您的银行身份。

这还不止于此。合法邮件也可能成为不公平待遇的受害者，但为什么呢？

有多少次你的电子邮件无缘无故地出现在了垃圾邮件文件夹里？你可能只是给你的客户/追随者发邮件，祝他们新年快乐，可能会有什么问题呢？

你可能已经做了功课，但可能有一个方面你没有考虑到:电子邮件的真实性。

## 信任邮件

电子邮件真实性用于证明到达客户收件箱的电子邮件来自已知且可识别的域。如果你经常给你的客户发邮件，那将是你的领域。

对于一个沉重的电子邮件发件人来说，这是一个伟大而强大的工具，因为它能够确保没有人会试图欺骗你的企业的身份。换句话说，这是你的域名(@ yourcompany.com)发送电子邮件，而不是别人，非法伪造它。

对于收件人来说，这也很好，因为当收到电子邮件时，如果真实性检查失败，您可以认为该电子邮件是非法的，因此不可信。

换句话说，电子邮件的真实性类似于为每个域名提供一个非常安全的社会安全号码或护照。你可以打赌，电子邮件服务器会“自动”对收到的每封邮件进行检查。

## 如何认证我的邮箱？

一般来说，有多种方法可以鉴别你的简讯和电子邮件。然而，有 4 种流行的方法来验证您的电子邮件，结合更多的方法在一起，确保更高水平的保护，你一定要知道。

更多的保护，防止有人伪造电子邮件代表你，更多的保护，防止被标记为狡猾的发件人，从而被标记为垃圾邮件发送者。

4 种最受欢迎的方法是:

*   防晒系数
*   SenderID
*   DKIM
*   域名密钥
*   DMARC

像 **SPF** 和**发件人 ID** 这样的方法需要你修改一些 DNS 参数。这样做基本上等于创建一个可以发送你的电子邮件的服务器的白名单。不管是你自己公司的服务器还是外部的。
另一方面，像 **DKIM** 和 **DomainKeys** 这样的方法会在你的电子邮件发送出去的时候修改并在邮件头中包含特殊的验证码。

大多数公共电子邮件收件箱提供商，如 Google Mail，Hotmail，Yahoo，AOL，甚至 Comcast，都会检查 SPF 和 DKIM 作为其接收电子邮件的认证方法。因此，如果你的客户/观众正在使用这些服务来检查他们的电子邮件，我建议你更加认真地对待电子邮件的真实性。

除了撰写有趣和有说服力的信息、尝试直呼客户名字(个性化)、分析客户如何阅读您的电子邮件(开放时间、地理位置)并根据他们的兴趣定制电子邮件(细分)以及维持一般的发送策略(越来越多的人在移动设备上打开电子邮件)之外，电子邮件认证非常重要。尤其是现在，垃圾邮件发送者和骗子越来越成为累赘。

因此，使用 SPF 和 DKIM 来证明您的电子邮件的真实性的优点是，它将有效地降低您的邮件被接收您的电子邮件的电子邮件服务标记为可疑的风险。这实际上意味着，你的电子邮件不太可能像未经认证的邮件那样，最终出现在垃圾邮件文件夹中。
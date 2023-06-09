# 如何破解应用程序的逻辑

> 原文：<https://infosecwriteups.com/how-to-hack-applications-logic-6b0219f0dd04?source=collection_archive---------0----------------------->

大家好，我决定写一篇关于在 web、移动和桌面应用程序中寻找逻辑错误的指南。实际上，这篇文章不仅仅是关于打破逻辑，如果你理解得好，它将引导你像黑客一样思考，这样，你可能还会发现许多不同类型的漏洞。

![](img/b53b094d1e539b202e1ce8d9327f9e89.png)

我是谁？

首先，我是谁？我不会谈论我的过去，但是，现在，我在一家与金融有关的公司工作，我正在做内部和外部渗透测试，主要是针对应用程序。我可以说，在 3 个月的时间里，我在不同的公司发现了近 30 个关键的逻辑漏洞。所以，我会试着向你展示我是如何找到它们的。我是如何发现漏洞给公司带来了数百万美元的损失。

![](img/c8d89cc696291edd79a0ddcb9ef154ff.png)

**为什么逻辑漏洞很重要？**

在我看来，寻找弱点与风格有关，我认为只关注自己公司的 pentester 应该在 2-3 年后离开。为什么？因为几乎每个黑客都有自己检查漏洞的风格。两年后，那双眼睛发现了他风格的所有弱点，你应该用另一双眼睛看得更远。第二个原因是我们在 2022 年，我认为在同一家公司工作 10 年已经过时了。最重要的原因是，总是不同的应用程序，系统和人会教你不同的东西，你必须退出你的舒适区。当然，你可以和自己一起努力提高自己，但真实的区域总是会推动你进一步学习。

有一种风格是寻找应用程序的逻辑以及如何打破它们。

逻辑漏洞之所以有价值，你应该去寻找，是因为没有自动化的工具来检查逻辑 bug，因为机器学习还没有学会学习。所以这就是为什么你必须学习应用程序做什么，为什么你不应该是一个自动化的机器人。；)

**我从哪个窗口看？**

![](img/bcd674e6b633fc2e791577848d57908f.png)

所以正如我所说的，我讨厌随意入侵。我的意思是，我讨厌在不了解应用程序的情况下尝试 XSS、SQL 有效负载或类似的东西。我知道你听说枚举是关键。但不仅仅是认证考试或者盒子。在现实生活中，如果你想知道你在黑什么，你应该了解应用程序是做什么的。

我没有使用任何路线图来列举应用程序或网络系统。然而，我可以建议在这个领域的新的人下面的链接。在你有自己的风格之前，你需要跟随人们的方式去学习。

[](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web#step-by-step-web-application-discovery) [## 80，443-pentest Web 方法

### 服务器的已知漏洞:运行的版本。响应的 HTTP 头和 cookies 可能是…

book.hacktricks.xyz](https://book.hacktricks.xyz/network-services-pentesting/pentesting-web#step-by-step-web-application-discovery) 

将来，我会在 gitbook 上发布我的笔记，所以不要忘记在这里查看我是否编辑过。

**开发者在构建应用时是如何思考的？**

我经历过一个有趣的商店，我想告诉你。有了这些，我想你会明白黑客和开发者的主要区别。

去年，我在一个在线购物应用程序中发现了一个关键的 IDOR，我联系了构建它的开发人员之一，以便一起修复它。会上有趣的事情是。

> ~开发者通过伪代码思考~
> 
> 如果客户 id 是 1234，
> 
> 获取 1234 的信息，
> 
> 如果客户 id 是 5678，
> 
> 获取 5678 的信息。

它看起来不像马车，对吧？至少对开发商来说不是。因为他觉得我们通过 1234 id 获取，应用发送 5678 信息的时候有问题。

![](img/593896aa10e21dde33bf6417cacf15e2.png)

但是开发商没有考虑到一件事。我们正在使用 1234 的会话获取 5678 的信息。问题从那里开始...

**逻辑错误从哪里开始，如何发现？**

就我讲的，都是关于为什么要学应用逻辑。现在我们来打破它们。如果你理解了应用程序的逻辑，你应该思考我们如何打破它的逻辑来使用它。

![](img/19315b59be3421031ea17d903f219d1c.png)

假设有一个登录面板，该面板有一些忘记密码的链接。

您应该创建帐户来测试它。别忘了，首先我们要理解他们，然后我们要打破他们！

我们看起来登录是清楚的，但是当我们检查忘记密码部分时，我们看到当我们单击忘记密码时，它说请输入您的狗的名字或他们想要的任何独特的东西。

您应该检查响应和请求，以便理解它们如何控制变量，以及我们是否可以操纵它们。

如果你知道它是 JSON 或者 SQLite，你不应该找到任何东西，你应该在 google 和 payload 上研究黑客和绕过技术。(【https://github.com/swisskyrepo/PayloadsAllTheThings】T4)

然而，大多数研究应该是关于理解应用。黑客 90%理解它，10%利用它。谷歌是我们最好的朋友，永远不要忘记用它来研究。

![](img/2b9f768ff5be2138d5a54e8217debcea.png)

让我们回到我们的例子，我们检查请求和响应，有一个控制参数检查狗的名字。我们应该明白什么反应是可以的，什么是不可以的。如果应用程序发送了不唯一的内容，或者黑客可以找到它，则存在逻辑帐户接管漏洞。因为即使开发人员检查请求输入，开发人员通常也会忘记黑客可以操纵响应。如果黑客可以在响应中找到密钥，他就可以操纵响应。不要对开发者感到震惊，这些耳朵听得太多了。:D 他们的思维方式确实和我们不同。也许来自每个人:D

**第二个例子:**

这并不是一个真正的逻辑错误，然而，我把它放在这里是为了向你展示你在黑客攻击时应该如何思考。

![](img/28478b0876064d74f12236830c7e89cf.png)

我正在测试一个网站，我看到有上传文件的功能。首先，我试着和大家一样上传了一个 shell。但是后来我发现有一个关于解析的错误。错误是我们仅次于谷歌的第二好朋友。他们是开发商的敌人，敌人的敌人是我们的朋友。:)他们给我们关于应用程序的信息，这是黑客攻击的黄金。在此之前，我做了枚举，我知道这是一个 ASP.net 应用程序，我们正在上传 xslx 文件，然后它解析它，在应用程序的另一部分显示给我们。

当我看到这里时，解析错误说我们找不到需要解析的部分。我开始通过谷歌研究 ASP.NET 是如何解析 xslx 文件的。

然后我看到，当我们解压缩 xlsx 文件时，有一个 XML 格式的文件，它包括 xslx 的标题。(excel 应用程序的 xslx 部分)和 ASP.NET 代码，在里面找。

其次，我想我怎么能伤害它，我能在里面放什么？

因为它是一个 XML 文件，我想我可以尝试 XXE 注射，但是如果你是新的，你应该寻找谷歌，我如何通过 XML 攻击。当你学会了它，在下一次你找到它的时候，你会像我一样思考。然后，我在其中创建了我的有效载荷，并重新构建了 xlsx，我就可以在应用程序中运行我的代码了。

这是一个攻击的例子:

[https://www.4armed.com/blog/exploiting-xxe-with-excel/](https://www.4armed.com/blog/exploiting-xxe-with-excel/)

[**让我们创建一个路线图吧！**](https://github.com/swisskyrepo/PayloadsAllTheThings)

1-了解应用程序的目标，以及它想为人类做什么。

2-列举应用程序的所有部分，并了解有多大。

3-了解应用程序的特性，它有什么样的特性，会出现什么样的漏洞。你迟早会在这方面做得更好。

4-开发人员在构建我们正在研究的功能时是如何思考的，我们如何将它用于其他事情？检查请求和响应参数。

5-不要觉得学习过程是浪费时间，试着去学习 app 是做什么的，有哪些功能可以错过开发者。

不要害怕思考，不要将一切自动化。

7-从邪恶的角度思考。是的，有时候你应该从窗户进入家里。也许你必须成为圣诞老人。:)

8-不要失去希望，每个由人类构建的应用程序甚至 openai 都收集人类的程序，以便创建程序。别忘了，如果有人类，就一定会有错误。

![](img/7a36477dd005d6547f323b84ec08b5e5.png)

我知道这就像搏击俱乐部的规则。我们不谈论搏击俱乐部的规则是。

！！了解应用程序做什么，并尝试做其他事情！！

**最终:**

感谢您的阅读，我独自一人在咖啡馆，我决定解释黑客逻辑和寻找逻辑漏洞的一些部分。

![](img/91f69a0ae5e39f402b758d9996be6837.png)

# 希望你喜欢它！

## 来自 Infosec 的报道:Infosec 每天都有很多内容，很难跟上。[加入我们的每周简讯](https://weekly.infosecwriteups.com/)以 5 篇文章、4 条线索、3 个视频、2 个 GitHub Repos 和工具以及 1 个工作提醒的形式免费获取所有最新的 Infosec 趋势！
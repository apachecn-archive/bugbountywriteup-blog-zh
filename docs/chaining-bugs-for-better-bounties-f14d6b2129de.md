# 为更好的奖金链错误

> 原文：<https://infosecwriteups.com/chaining-bugs-for-better-bounties-f14d6b2129de?source=collection_archive---------0----------------------->

![](img/3d5401c7e2fb63adc912ce3a53c66f00.png)

来源:谷歌

将一些低级别的 bug 链接到更高级别总是很有趣，同时也很有挑战性，最好的事情是如果你成功了，你会得到更高的奖励。我一直想写一个关于它的博客，但我在等待一些个人场景来更好地解释它，现在我觉得这是谈论这件事的正确时间:)

嗨，伙计们，我希望你们都做得很好，取得巨大的进步。正如标题所言，这个博客将会把一些场景升级为一些高级错误。我将尽可能简单地解释它。在我们开始之前，让我告诉你，如果你对 bug 奖励/pentesting 还比较陌生，我强烈建议你学习一些编程来理解链接。当你至少掌握了理解代码流的知识时，你就可以很好地链接东西了。我的场景可能与编程没有直接关系，但从长远来看你会需要它:)

最近，我发现了 3-4 个 bug，如果我没有链接它们，它们很容易被拒绝。有些场景很复杂，有些充满了学问。当你独自研究不同的东西时，你会学到很多东西，因为那时你完全专注于你的研究。好吧，我们先从心态开始。很多新人都有这个问题，他们收到很多拒绝。**记住这个东西，2021 和 2016–17 有 5 年的差距，bug 赏金这些年变化很大。许多低级错误过去在 2015-18 年被接受，现在不在范围内。我想解释的是，当你遇到这样一个 bug 时，想想你还能做些什么。可能有多种方法来提高 bug 的严重性。**

谈够了，让我们先看看我们的**的**场景。我有一个场景，我们可以上传文件并下载它们。所以一旦你下载了文件，它会给你一个 URL 路径。大概是这样的:

【https://target.com/】****用户/公众？download path = https://vuln . com****

**你猜对了吗？我在这里得到了一个 **SSRF** ，它的影响很小，因为我不能用它做任何事情。我只是在 collaborator 服务器上找到一个匹配，仅此而已。我在研究我们还能用它做什么。然后，我想如果我们能把它重定向到一个不同的服务器(自己的),那肯定会有一些意义。嗯，在这里我必须研究一些东西，因为这里有两件事。首先，重定向应该是正确的，其次，执行应该是准确的。如今，URL 重定向在很多情况下也是不被接受的。所以我继续，托管了我自己的服务器，上传了一个 XSS 脚本，并将目标 URL 重定向到这个服务器，就像这样**

**[**https://target.com/**](https://target.com/)**user/public/download path = https://own server . com/XSS . html****

**所以现在，如果有人访问这个网址，他们会得到一个弹出窗口，可能会有多个场景的一个 **XSS** :) Vuln 被接受，即使他们接受它作为中低，它增加了影响。**

**![](img/c248980e7e19fe7ee1e3211e80b06246.png)**

**来源:谷歌**

**第二个**案例是，我在一个众所周知的目标上狩猎，超过 400 个 bug 被接受。老实说，我不是在找 bug，我只是想试试运气，看能不能找到什么。所以在一个子域上，我发现了 **/wp-json/wp/v2/users** 这本身不是 bug。不要随便举报只是为了增加举报次数 lol。众所周知，在这个文件夹中，我们得到了名字和 id 以及更多的数据。所以我想如果我们能在这个组织的 GitHub 上搜索这个人。我用了这个笨蛋:****

****组织:目标“用户名”****

**这是一个惊喜。这个人在这里有一个回购协议，我们得到了违约凭证。当然不是 **admin:admin** 但足以登录该帐户。不幸的是，他没有这样的特权，他只是一个开发者。我把它上报了，它在那里被接受了，足足 600 美元。**

**在这些案例中，我发现探索这些东西真的很有趣。不要认为这两个错误是小菜一碟，因为我已经总结了这些在短期内。这花了一些时间，特别是第一次，因为我在自己的服务器上有太多的错误。这都是一些运气，没有人注意到它，直到那时，它出来作为对我的奖励:)**

**我写这个只是为了让人们知道，特别是新手，不要在没有对任何发现进行多次研究的情况下放弃。已经有人把 P5 的 bug 升级到临界了。到处搜索解决方案，如果你擅长编程，你可以多次找到自己的方法。举个例子，如果你上传了一个文件，尝试所有可能的方法来进一步升级它。上传几乎所有的东西，看看应用程序是否允许你上传类似脚本的东西。改变扩展名，增加一个额外的扩展名，这些东西肯定会帮助你学到很多东西。此外，始终留意每个经过端点的 URL。默认参数对升级 SSRFs 非常有帮助。**

**当我们谈论 XSS 时，它并不局限于经典作品。尝试在应用程序中寻找 DOM 值，JS 会在这方面给你很大帮助。DOM XSS 升级有点棘手，但他们也有更高的收益，有时你可以在操作 DOM 时找到一个站点范围的 XSS。**

**这将是这一次，我希望你能从这里学到一些东西:)如果你做到了，请与社区分享，我非常感谢。你也可以在 **twitter/LinkedIn** 上关注我，询问任何与 AppSec、bug 奖金和 pentesting 相关的事情。祝你一切顺利:)**

**保重，快乐黑客！**

**Adios❤**

**推特:- **manasH4rsh****

**领英:-[玛纳斯苛刻 ](https://www.linkedin.com/in/manasharsh/)**
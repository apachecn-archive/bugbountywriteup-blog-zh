# 入侵防御系统(IPS)如何在防火墙中工作

> 原文：<https://infosecwriteups.com/how-intrusion-prevention-systems-ips-work-in-firewall-b64dd782e502?source=collection_archive---------2----------------------->

入侵防御和防火墙是网络威胁防护的一部分。网络威胁防护和内存利用缓解是网络和主机利用缓解的一部分。

入侵防御自动检测和阻止网络攻击。在 Windows 计算机上，入侵防御还会检测和阻止对支持的浏览器的浏览器攻击。入侵防御是继防火墙之后保护客户端计算机的第二层防御。入侵防御有时也称为入侵防御系统(IPS)。

入侵防御在网络层拦截数据。它使用签名来扫描数据包或数据包流。它通过寻找与网络攻击或浏览器攻击相对应的模式来单独扫描每个数据包。入侵防御检测对操作系统组件和应用层的攻击。

什么是入侵防御系统(IPS)？

入侵防御系统(IPS)是一种安全解决方案，可在网络级别提供安全保护，防止未经授权的访问和恶意活动。与只监控网络流量的入侵检测系统不同，入侵防御系统还可以防止网络上发生的入侵。入侵防御系统的主要功能是分析所有入站和出站网络流量中的可疑活动，并立即执行适当的操作，以防止入侵者进入内部网络。

IPS 通过阻止有害网络流量到达其目标受害者，主动检测和防范有害网络流量。正确部署的 IPS 会立即丢弃检测到的有害或恶意数据包，这些数据包可能会对网络和网络资源造成严重损害。入侵防御系统可以非常方便地抵御各种网络安全攻击，如暴力攻击、拒绝服务(DoS)攻击、漏洞检测。此外，IPS 还确保防止协议漏洞。
入侵防御系统也被称为主动安全解决方案，因为它不仅检测网络上的潜在安全威胁，而且还立即采取措施应对这些威胁，以防止当前的攻击以及入侵者在未来可能发起的类似攻击。

入侵防御系统可以执行的其他功能包括:

*   阻止来自违规源 IP 地址的网络流量。
*   重置 TCP 连接
*   纠正未分段的数据包流
*   纠正循环冗余校验(CRC)错误
*   检查 TCP 排序问题
*   清理未经请求的传输和网络层选项。

入侵防御系统是如何工作的？

与入侵检测系统相比，入侵防御系统被认为是非常安全的解决方案，因为它具有主动的威胁检测和预防能力。入侵防御系统以串联模式工作。它包含一个直接位于实际网络流量路由中的传感器，当数据包通过它时，它会深入检查所有网络流量。串联模式允许传感器在预防模式下运行，执行实时数据包检测。因此，任何识别出的可疑或恶意数据包都会被立即丢弃。

入侵防御系统在检测到网络中的任何恶意活动时，可以执行以下任何操作:

*   终止被外部人员利用进行攻击的 TCP 会话。它会阻止试图不道德地访问目标主机、应用程序或其他资源的违规用户帐户或源 IP 地址。
*   一旦 IPS 检测到入侵事件，它还可以重新配置或重新编程防火墙，以防止将来发生类似的攻击。
*   IPS 技术也足够智能，可以替换或删除攻击的恶意内容。当用作代理时，IPS 控制传入的请求。为了执行这项任务，它重新打包有效负载，并删除传入请求中包含的标头信息。它还能够在将电子邮件发送给内部网络中的收件人之前，从电子邮件中删除受感染的附件。

入侵防御系统使用四种方法来保护网络免受入侵，包括:

*   基于签名—在基于签名的方法中，知名网络攻击的预定义签名或模式由供应商编码到 IPS 设备中。然后，通过将攻击包含的模式与 IPS 中存储的模式进行比较，使用预定义的模式来检测攻击。这种方法也被称为模式匹配方法。
*   基于异常—在基于异常的方法中，如果在网络中检测到任何异常行为或活动，IPS 会根据管理员定义的标准阻止其访问目标设备。这种方法也称为基于配置文件的方法。
*   基于策略—在基于策略的方法中，管理员根据其网络基础设施和组织策略将安全策略配置到 IPS 设备中。如果活动试图违反配置的安全策略，IPS 会触发警报，提醒管理员注意恶意活动。
*   基于协议分析—这种方法有点类似于基于签名的方法。基于签名的方法和基于协议分析的方法之间的唯一区别是，与基于签名的方法相比，后者可以执行更深入的数据包检查，并且在检测安全威胁方面更具弹性。

入侵防御系统的类别

*   基于主机的入侵防御系统(HIPS) —基于主机的入侵防御系统是安装在特定系统(如服务器、笔记本电脑或台式机)上的软件应用程序。这些基于主机的代理或应用程序仅保护安装它们的特定主机上运行的操作系统和应用程序。基于主机的 IPS 程序要么从一端阻止攻击，要么命令操作系统或应用程序停止攻击发起的活动。
*   基于网络的入侵防御系统(NIPS) —基于网络的 IPS 设备在网络参数内以串联模式部署。在基于网络的 IPS 中，会检查通过它的所有传入和传出网络流量是否存在潜在的安全威胁。一旦 IPS 发现攻击，它就会拦截或丢弃恶意数据包，以防止其到达预定目标。

集成了基于网络的 IPS 功能的防火墙至少包含两个网络接口卡(NIC)。一个被选为内部网卡，并连接到组织的内部网络。另一个网卡被选为外部网卡，并连接到外部链路，在大多数情况下是互联网。

当流量在任一网卡处被接收时，它会被集成网卡的检测引擎进行深度检查。如果 NIPS 察觉到恶意数据包，它会立即丢弃该数据包，并向网络安全人员报警。在检测到来自源的单个恶意数据包后，它会立即丢弃来自该特定 TCP 连接的所有其他数据包，或者永久阻塞会话。
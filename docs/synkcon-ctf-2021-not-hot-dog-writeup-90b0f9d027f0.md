# 先科康 CTF 2021 不吃热狗报道

> 原文：<https://infosecwriteups.com/synkcon-ctf-2021-not-hot-dog-writeup-90b0f9d027f0?source=collection_archive---------3----------------------->

![](img/d9ece47518b618a8e5e9151b5cee1614.png)

给定的文本文件包含 n、e 和 c 的值，这是一个 RSA 解密挑战。

```
n = 609983533322177402468580314139090006939877955334245068261469677806169434040069069770928535701086364941983428090933795745853896746458472620457491993499511798536747668197186857850887990812746855062415626715645223089415186093589721763366994454776521466115355580659841153428179997121984448771910872629371808169183
e = 387825392787200906676631198961098070912332865442137539919413714790310139653713077586557654409565459752133439009280843965856789151962860193830258244424149230046832475959852771134503754778007132465468717789936602755336332984790622132641288576440161244396963980583318569320681953570111708877198371377792396775817
c = 580087704654652718548072347767087713441678375071000498564963353235374511777098333485190394366859651200453688757231829505858552725280311870462095017761444727880100748324874906835296769310122754627620933554008332091299159978573396458947155647454747215038440028347688779707172885517390987973184407689583941483511
```

我们可以使用 RsaCTFTool 来查找明文。

```
python3 RsaCtfTool.py -n 609983533322177402468580314139090006939877955334245068261469677806169434040069069770928535701086364941983428090933795745853896746458472620457491993499511798536747668197186857850887990812746855062415626715645223089415186093589721763366994454776521466115355580659841153428179997121984448771910872629371808169183 -e 387825392787200906676631198961098070912332865442137539919413714790310139653713077586557654409565459752133439009280843965856789151962860193830258244424149230046832475959852771134503754778007132465468717789936602755336332984790622132641288576440161244396963980583318569320681953570111708877198371377792396775817 --uncipher 580087704654652718548072347767087713441678375071000498564963353235374511777098333485190394366859651200453688757231829505858552725280311870
462095017761444727880100748324874906835296769310122754627620933554008332091299159978573396458947155647454747215038440028347688779707172885517390987973184407689583941483511
```

flag:SNYK { b 6 e 04 ce 500 f 9d 998 b 8 AC 412d 7 a 85 e 359 ca 8 b 7 fc 31267 cd6f 7182d 57 E6 c 39 a2 ea }
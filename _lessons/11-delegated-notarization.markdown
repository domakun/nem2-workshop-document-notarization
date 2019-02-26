---
layout: post
title:  "委托公证"
permalink: /lessons/delegated-notarization/
---

# 背景

公共网络需要收费来发布交易。Bob想要公证数字文档，但他对XEM或者对区块链技术没有有足够的了解。因此他选择将复杂的部分委托给专门的公证服务

Bob将使用他的帐户签署文件内容。在将文件的哈希码发送给专业公司之后，专业公司将帮Bob把转让交易发布到区块链。

他可以通过使用账户对内容进行签名证明他已经得知该文件的内容。

![delegated-notarization]({{ site.baseurl }}/assets/images/diagram-delegated-notarization.png)

## 实现方法

1\. 创建一个新帐户以代表公证公司。

{% highlight bash %}
$> nem2-cli account generate
Introduce network type (MIJIN_TEST, MIJIN, MAIN_NET, TEST_NET): MIJIN_TEST
Do you want to save it? [y/n]: y
Introduce NEM 2 Node URL. (Example: http://localhost:3000): http://localhost:3000
Insert profile name (blank means default and it could overwrite the previous profile): company
New Account:    SADJMU-JPDQ3U-N5HARH-74U4FP-XLHRA7-DCGQKN-SSOI
Public Key:     76386325576C2536F1BA239CE4FA8F24E0EBA0F2CF982C0AB1C7D928A2ECDC10
Private Key:    A2...D5
{% endhighlight %}

2\. 打开``Create Notarization``选项卡。拖放Bob的文件（您可以使用之前的txt）。使用他的帐户签署文件的内容。

![screenshot-delegated-notarization]({{ site.baseurl }}/assets/images/screenshot-delegated-notarization.png)

3\. 生成的签名将添加为交易的消息（message）。通过使用服务的私钥公证交易。

您可以选择使用服务提供商的地址作为公证的接收帐户。


4\. 当事务在块中保存后，Bob就可以验证文件的内容是否已使用自己帐户对其进行签名。

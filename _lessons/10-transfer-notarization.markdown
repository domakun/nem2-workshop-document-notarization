---
layout: post
title:  "转让公证"
permalink: /lessons/transfer-notarization/
---

## Background

Alice想把公证书转交给Bob。公证类型是 **2-of-2 multisig**。 回顾前一个模块，只有cosignatories能够在multisig账号宣布交易。 如果Alice把她自己从cosignatories中删除（remove），Bob将是唯一一个允许其发布交易的人。

multisig合约 **editable（可编辑）**。Alice可以更改multisig帐户合同，把自己从账户中删除。 我们将``minRemoval``设置为1，因此从帐户中删除某人只需要一个cosignature。

从此时起，Bob将成为唯一允许从该帐户转移交易的人。 公证类型将成为 **1-of-1 multisig**。

![diagram-transfer]({{ site.baseurl }}/assets/images/diagram-transfer.png)

## 实现方法

1\. 打开 ``Create multisig``标签页并点击``Edit multisig``.

{% highlight bash %}
$> nem2-cli account generate
Introduce network type (MIJIN_TEST, MIJIN, MAIN_NET, TEST_NET): MIJIN_TEST
Do you want to save it? [y/n]: y
Introduce NEM 2 Node URL. (Example: http://localhost:3000): http://localhost:3000
Insert profile name (blank means default and it could overwrite the previous profile): bob
New Account:    SBTFDZE4RTETKCTGNLIV4HL6ACLZIHUDBVAKACOB
Public Key:     EB770736BC20FF07682849A067423E679C7E2167BAB3CA33DE2EF9B0D088F4EF
Private Key:    88...92
{% endhighlight %}

2\. 填表:

* **Signer private key**（签名者私钥）: Alice的私钥；
* **Multisig public key**（Multisig公钥）: 公证的公钥（确定性）；
* **Cosignatories to remove**（要删除的签名者）: Alice的公钥；
* **Min Approval Delta**（最小批注增量）:-1。 当我们删除其中一个cosignatories，并且minApproval设置为2时，减去1使其成为 1-of-1。

![screenshot-edit-multisig-account]({{ site.baseurl }}/assets/images/screenshot-edit-multisig-account.png)


3\. 单击``Edit multisig``按钮。 把``minRemoval``设置成1,Bob已经没有签署交易的需求了。等待直到收到网络确认交易的信息。

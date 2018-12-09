---
title: "Cashport基于比特币现金的登录授权工具"
date: 2018-10-15T16:41:52+08:00
draft: true
---

最近handcash团队推出了一个登录授权SDK，名为[cashport](https://cashport.io)，它可以让用户
很方便地登录第三方应用并使用BCH进行收付款。我们第一时间更新到了最新款的handcash钱包，来测试一下这个新功能。

<!--more-->

在最新版的handcash钱包的设置页面，多出了一栏名为cashport的设置项，其中包括“个人信息”（可以填写
姓名和邮箱），和“已连接的服务”（当在第三方应用登录之后，会在这里显示）。

![setting](/images/cp1.jpeg)

一般，用户登录第三方应用的时候，有这几个参与方：

- 用户
- 第三方应用
- 账号服务商

之间的信任关系是这样的：

- 用户想要使用自己的账号登录第三方应用，但只提供有限的个人信息。
- 第三方应用想要获取一些用户信息，并且确认用户登录的真实性。
- 账号服务商满足了用户和第三方应用的需求。

在传统的账号认证服务（微信，google，github）中，用户需要先登录这些账号，然后再授权（例如在手机微信
中点击一下）。cashport授权登录的流程是这样的：

## part.1
- 第三方应用从handcash官方获得一个 API_ID
- 第三方应用集成cashport sdk

## part.2
- 用户需要安装有handcash钱包，并注册自己的$handle。（handle是一个唯一的用户名，可作为收款的地址。）
- 用户在handcash钱包中填写个人信息，包括姓名和邮箱。

## part.3
- 用户打开第三方应用，点击“使用handcash登录”
- 如果是在安装了handcash的手机上，就会自动打开handcash。

如果没有安装handcash，则会显示一个二维码，内容包括：
```
handcash://cashport.app/auth?
app_id=L77MZzEO72ZZSrRg58ysiGvveqFe51rK9lMDXKILD6YJf4lNibacSUx0xr979duv&
personal_info=handle,first_name,last_name,email&
channel_id=69ebc9de43a1ea8586d04a8013e111d961026e1fa6e60493aa240dea2907142a66db872e5830903e1456dee0ed2abec13676c44386bc87e2b6ca1fbb2929fbff
```

这里的`channel_id`是由sdk生成的，每次刷新都会变化。然后可以使用handcash来扫码。

- 接下来在handcash里，可以看到应用的名称，和所需的个人信息，以及选择充多少钱，也可以选择0元，即
只登录不充钱。

![connect](/images/cp2.jpeg)

目前，在我的🔨手机上，每次走到这一步handcash就崩溃了，handcash的ceo Alex表示他们会尽快修复问题。

![fix](/images/cp3.jpeg)

最后，让我们来看一下cashport的愿景：“一个简单易用的全球支付系统，只为比特币(BCH)”

![vision](/images/cp4.jpeg)

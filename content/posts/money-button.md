---
title: "MoneyButton 初体验"
date: 2018-09-17T16:19:38+08:00
draft: false
---



听说 yours 公司最新推出了一款叫 MoneyButton(钱钮) 的产品，可以在你的网站上快速集成比特币(BCH) 支付。我决定来尝试一下。
<!--more-->


## 注册钱钮账号

无论是使用钱钮收款还是付款，都需要先拥有一个钱钮账号。进入 https://www.moneybutton.com ，进行注册。
注册账号时还需要保存一份12词的助记词，根据 [moneybutton的推特](https://twitter.com/money_button/status/1041370944869040128),
这个助记词是你的HD钱包的私钥。

## 在个人网站上集成钱钮

注册成功后，点击 "Get my money button"，即开始定制你的钱钮控件，生成的代码大概是这样的：

```html
<!-- This line should go where you want to put your button -->
<div class="money-button"
  data-to="390"
  data-amount="3"
  data-currency="CNY"
  data-label="CN¥3 打赏的感觉真爽"
  data-hide-amount="false"
  data-client-identifier="a487dbab0a83557b5b681456038be735"
  data-button-id="1537174392500"
  data-button-data="{}"
  data-type="tip"
></div>
<!-- This line can go anywhere -->
<script src="https://api.moneybutton.com/moneybutton.js"></script>
```

控件里的参数是可以自己设置的，还有[更多的参数](https://docs.moneybutton.com/docs/html.html)。
可以利用这些参数实现更复杂的商品下单付款等等功能。
把代码复制到你的个人网站页面里，就可以接受BCH打赏或者支付了。

## 充值钱钮账号

要使用钱钮进行付款，首先需要往你的钱钮账号里进行充值。

![mb1](/images/mb1.jpeg)

我用 handcash 钱包充值了 3.1元人民币，钱钮支持0确认，一瞬间就到账了。尴尬的是，由于汇率数据源不同，只显示到账 2.95元。

![mb2](/images/mb2.jpeg)

## 使用钱钮支付

登陆钱钮账号，充值完成，就可以在集成了钱钮控件的网站上进行支付了，不需要再频繁登陆各种账号，也不再需要打开手机扫码支付了。这种感觉只能用“如丝般顺滑”来形容，在本文末尾就可以亲自体验一下。

## 自己保管钱钮私钥

我试着把钱钮的助记词导入到其它钱包，步骤有些繁琐，使用Bitpay钱包：

1. 新建BCH钱包，"new personal wallet"
2. "show advanced option" -> "wallet key" -> "specify recovery phrase.."
3. 输入助记词，Deriviation Path 使用默认的 m/44'/0'/0'
4. 进入主界面的 "setting"，选择刚才新建的钱包
5. "More options" -> "Wallet address" -> "Scan addresses for funds"
6. 扫描完成后就可以看到转账记录了

目前BCH钱包的用户体验还是不够好啊，还有很大的改善空间 :)

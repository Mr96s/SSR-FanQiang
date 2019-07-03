# 搭建属于自己的 SSR 科学上网（翻墙）服务器

## 【小白/图文攻略】

**本文介绍怎么运用 VPS 快速搭建 SSR 服务。图文结合，简略具体，主要针对小白用户。
<br>多的技术原理在这里就不多说了，直接开始傻瓜式教程。**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/images.png)


首先我们需要一台国外的 vps 服务器 ,如果有了可以直接跳转的到搭建步骤。

没有的话这里推荐 [**vultr**](https://www.vultr.com/?ref=7326301) （之所以选择 vultr 是因为他支持支付宝）

# 一、创建服务器

## 1、账号注册

**首先打开**

### [Vultr 官网](https://www.vultr.com/?ref=7326301)

vultr 经常有注册优惠活动，查找最新可用优惠活动参考：[**vultr 最新优惠活动**](https://mr96s.com/718.html)

**打开后是这样一个注册界面**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/vultr%E9%A6%96%E9%A1%B5.png)

**Email Address** 输入你的邮箱地址

**PasswordP** 输入你想设置的密码 （密码组成要求按图上设置）

然后点击 **Ceate Account** 创建账户

**邮箱验证**

此时你的邮箱会收到一封验证邮件 去邮箱打开邮件进行验证就可以登陆了

**充值 vultr**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E5%85%85%E5%80%BC.png)

点击 **Billing** 账单来到充值页，选择支付方式和金额

然后点击 **Pay with Alipay** 用支付宝支付就可以生成支付宝付款二维码

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E6%94%AF%E4%BB%98%E5%AE%9D%E4%BB%98%E6%AC%BE.png)

## 2、添加服务器

点击Vultr后台右侧的蓝色**加号**，进入购买页面

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E5%88%9B%E5%BB%BA%E6%9C%8D%E5%8A%A1%E5%99%A8.png)

购买服务器，首先**选择机房位置** （建议选择**美国西海岸** 和 **亚洲机房**：洛杉矶、西雅图、新加坡、日本等，理论距离越近延迟越低，非绝对，和地区网络运营商也有一定关系）

**选择CentOS系统** 建议（7 x64）

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E9%80%89%E6%8B%A9%E7%B3%BB%E7%BB%9F.png)

**选择套餐**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E9%80%89%E6%8B%A9%E5%A5%97%E9%A4%90.png)

**勾选其它服务**

勾上前两个选项就行 (有些时候只有免费的 IPv6 那就只勾上他)

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E5%8B%BE%E9%80%89%20IPV6.png)

**填写主机名**

随便填个主机名，最好是英文的，**不填也可以**，点击 **“Deploy Now”** （现在部署） 即可

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E4%B8%BB%E6%9C%BA%E5%90%8D.jpg)

**然后等待安装  可能需要几分钟**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%BB%86%E8%8A%82.png)

安装好后，**查看服务器细节**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E9%9D%A2%E6%9D%BF%E4%BF%A1%E6%81%AF.png)

这里需要记住几个东西，可以创建个文本记下来。

**服务器ip地址      （IP Address）**

**用户名                （Username）**

**密码                    （Password）**

## 3、下载服务器连接工具

连接服务器用的是 ssh 连接工具，不管什么系统，只要是通过 ssh 协议都可以连接

**Windows** 推荐用  [**xshell**](https://sm.myapp.com/original/net_app/xshell5_wm_5.0.1332.exe)  来连接，百度下载安装一个就行 （有360的直接在软件管家搜索xshell下载）

[**腾讯软件中心 Xshell 下载直达**](https://sm.myapp.com/original/net_app/xshell5_wm_5.0.1332.exe)

**Mac** 和 **Linux** 可参考：[**Mac/Linux 如何使用 SSH 连接 VPS 服务器**](https://mr96s.com/813.html)

安装 xshell 后，打开软件。

点击 **“文件”** → **“新建”** → **“连接”**

输入 **“名称”** 和 **“主机”** （即VPS IP）。

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/xshell%20IP.png)

选择 **用户身份验证** 输入服务器用户名和密码 登陆服务器

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/xshell%E7%94%A8%E6%88%B7%E5%90%8D%E5%AF%86%E7%A0%81.png)

**键盘** 设置下，不然使用不了 **清除 键**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E9%94%AE%E7%9B%98%E8%AE%BE%E7%BD%AE.png)

确定 连接，接受并保持密码，下次连接就不用再输密码了

**连接成功**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E8%BF%9E%E6%8E%A5%E6%88%90%E5%8A%9F.png)

若无法连接成功参考：[**Vultr 服务器无法连接解决方法**](https://mr96s.com/1000.html)

## 4、部署 SSR 服务端

**依次执行以下三行命令**  (复制到 Xshell 右键粘贴)

```
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh


chmod +x shadowsocks-all.sh

./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E5%AE%89%E8%A3%85%E5%91%BD%E4%BB%A4.png)

按照提示操作

这里让你选择安装的服务端版本 **选择 2**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E9%80%89%E6%8B%A9%E6%9C%8D%E5%8A%A1%E7%AB%AF%E7%89%88%E6%9C%AC.png)

这里**设置密码**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E8%AE%BE%E7%BD%AE%E5%AF%86%E7%A0%81.png)

这里**设置端口** （最好不要设置443和8080，以免占用）回车

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E8%AE%BE%E7%BD%AE%E7%AB%AF%E5%8F%A3.png)

选择**加密方式** 我这里选择 chacha20 

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E8%AE%BE%E7%BD%AE%E5%8A%A0%E5%AF%86%E6%96%B9%E5%BC%8F.png)

选择协议 auth_shal_v4

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E5%8A%A0%E5%AF%86%E5%8D%8F%E8%AE%AE.png)

选择**混淆方式** tlsl.2_ticket_auth

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E6%B7%B7%E6%B7%86.png)

**任意键继续**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E4%BB%BB%E6%84%8F%E9%94%AE%E7%BB%A7%E7%BB%AD.png)

等待两分钟

提示 **enjoy it ! ，即安装成功**

**（红色部分可以看到你配置的信息，也是关键信息最好复制下来）**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E7%BA%A2%E8%89%B2%E8%BF%94%E5%9B%9E%E4%BF%A1%E6%81%AF.png)

这里基本上就成功了    

只需要在电脑或者手机等 终端设备安装客户端连接即可完成

## 5、安装 SSR 客户端

下载 SSR 客户端连接。包含 win、mac 和 安卓客户端。

客户端下载链接（都是 GitHub 开源地址）：

**安卓：**[**shadowsocks-android**](https://bwghost.net/go/?url=https://github.com/shadowsocksr-backup/shadowsocksr-android/releases/download/3.4.0.8/shadowsocksr-release.apk)

**Windows：**[**shadowsocks-windows**](https://bwghost.net/go/?url=https://github.com/shadowsocksr-backup/shadowsocksr-csharp/releases/download/4.7.0/ShadowsocksR-4.7.0-win.7z)   （win 8及以上系统打开 4.0.exe，win 7则打开 2.0.exe）

**Mac：**[**ShadowsocksX-NG-R**](https://bwghost.net/go/?url=https://github.com/qinyuhang/ShadowsocksX-NG-R/releases/download/1.4.4-r8/ShadowsocksX-NG-R8.dmg)

[**其它版本**](https://github.com/shadowsocksr-backup/)



下载下来，解压打开      如图所示：

**密码，端口以及加密方式必须与上面复制下来的红色信息一致**

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E7%99%BB%E9%99%86%E5%AF%B9%E5%BA%94.png)

点击确定，在托盘中 右键 小飞机可以进行一些设置

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/%E5%8F%B3%E9%94%AE%E5%B0%8F%E9%A3%9E%E6%9C%BA.png)


手机等其他平台和电脑一样，填入对应连接信息，启用即可。其他选项如果不懂的话，保持默认就好。

:feet::feet::feet: **完成！现在就可以访问 Google 啦** :feet::feet::feet:



## 6、优化  （强烈建议优化）

优化后速度会有几倍的提升，可以先试用几天再来优化。

[**一键安装谷歌 BBR 优化加速**](https://mr96s.com/96.html)


*此为 5 $ 服务器优化后效果，4 K 秒播*

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/4k%E7%A7%92%E6%92%AD.png)

![](https://github.com/Mr96s/SSR-FanQiang/blob/master/picture/4k%E7%94%BB%E8%B4%A8.png)


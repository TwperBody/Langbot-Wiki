# 部署消息平台 Lagrange

## Lagrange介绍

Lagrange 是一个 QQNT 协议逆向工程框架，轻便且相对稳定。通过 OneBot 11 协议接入，需选择使用`OneBot v11`作为适配器。

::: warning
需要使用 NT QQ 与机器人交互，旧版QQ无法正常使用
:::

## 部署步骤

以下仅提供 Windows 上的大致步骤，详细步骤或其他平台请参考 [Lagrange官方文档](https://lagrangedev.github.io/Lagrange.Doc/v1/Lagrange.OneBot/)

### 环境配置

安装.NET 8运行时，[点击直达微软官网下载](https://dotnet.microsoft.com/zh-cn/download/dotnet/thank-you/runtime-desktop-8.0.4-windows-x64-installer)

### 从Github Actions下载最新的build

需要登录Github后才能下载，如果你不需要部分特性，可以在Release下载，看图片3

[Github Actions](https://github.com/KonataDev/Lagrange.Core/actions)  

看图进行下载:

![图片1](/assets/image/zh/deploy/bots/qq/onebot/lagrange/dl_lgr_1.png)

![图片2](/assets/image/zh/deploy/bots/qq/onebot/lagrange/dl_lgr_2.png)

![图片3](/assets/image/zh/deploy/bots/qq/onebot/lagrange/dl_lgr_3.png)

### 尾声

解压你所下载的zip，打开到有Lagrange.OneBot.exe的目录，在此目录下打开cmd命令提示符，输入

```bash
.\Lagrange.OneBot
```

运行一次，如果输出了一个二维码，即可直接用机器人号扫码登录（若二维码显示不清楚，可以到lagrange的data目录下寻找图片文件）。  

若无法登录，请检查是否正常填写了lagrange配置文件appsettings.json中的签名地址 SignServerUrl ，签名地址请到lagrange文档中寻找。  

## 修改配置

需要配置 Lagrange 以让其连接上 LangBot，请编辑 Lagrange 的配置文件 appsettings.json，确保 Implementations 中的连接配置符合下图内容：

![配置连接](/assets/image/zh/deploy/bots/qq/onebot/lagrange/config_lgr.png)

其中 Type 必须为 `ReverseWebSocket`;  
Host 为 LangBot 运行的主机 IP，若在同一主机上，可以写 `127.0.0.1`；   
Suffix 必须为 `/ws`；  

## Lagrange 对接

接下来打开 LangBot 配置页面

点击机器人，点击添加

`平台/适配器选择`为`OneBot v11`

![napcat_webui_03](/assets/image/zh/deploy/bots/qq/onebot/napcat/napcat_webui_03.png)

::: info
注意，如果涉及多个 docker 容器的网络连接问题，请参考[网络配置详解](/zh/workshop/network-details)
:::
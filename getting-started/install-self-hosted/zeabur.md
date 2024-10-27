# 部署 Dify 到 Zeabur

[Zeabur](https://zeabur.com) 是一个服务部署平台，可以通过一键部署的方式部署 Dify。本指南将指导您如何将 Dify 部署到 Zeabur。

## 前置要求

在开始之前，您需要以下内容：

- 一个 Zeabur 账户。如果您没有账户，可以在 [Zeabur](https://zeabur.com/) 注册一个免费账户。
- 升级您的 Zeabur 账户到开发者计划（每月 5 美元）。您可以从 [Zeabur 定价](https://zeabur.com/pricing) 了解更多信息。

## 部署 Dify 到 Zeabur

Zeabur 团队准备了一个一键部署模板，您只需点击下面的按钮即可开始：

[![Deploy to Zeabur](https://zeabur.com/button.svg)](https://zeabur.com/1D4DOW)

点击按钮后，您将被导航到 Zeabur 上的模板页面，您可以在那里查看部署的详细信息和说明。

<figure><img src="../../.gitbook/assets/zeabur-template-overview.jpeg" alt="Zeabur Template Overview"><figcaption></figcaption></figure>

点击部署按钮后，您需要输入一个生成的域名，以便将域名绑定到您的 Dify 实例并注入到其他服务中作为环境变量。
然后选择您喜欢的区域，点击部署按钮，您的 Dify 实例将在几分钟内部署完成。

<figure><img src="../../.gitbook/assets/zeabur-region-select.png" alt="Select Region"><figcaption></figcaption></figure>

部署完成后，您可以在 Zeabur 控制台中看到一个项目页面，如下图所示，您在部署过程中输入的域名将自动绑定到 NGINX 服务，您可以通过该域名访问您的 Dify 实例。

<figure><img src="../../.gitbook/assets/zeabur-project.png" alt="Zeabur Project Overview"><figcaption></figcaption></figure>

你也可以在 NGINX 服务页面的 Networking 选项卡中更改域名。您可以参考 [Zeabur 文档](https://zeabur.com/docs/deploy/domain-binding) 了解更多信息。
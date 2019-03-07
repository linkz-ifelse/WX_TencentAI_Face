使用腾讯云[人脸识别](https://cloud.tencent.com/product/FaceRecognition)API在小程序上轻量级人脸识别Demo，分为**1.0版（Server：Docker+PHP）**和**2.0版（Server：NodeJS+小程序云开发）**

![](https://techeek-cn-1251732175.cos.ap-chengdu.myqcloud.com/wx_AI_face/Snipaste_2018-12-14_17-02-37.png)

**Demo演示**

![](https://techeek-cn-1251732175.cos.ap-chengdu.myqcloud.com/wx_AI_face/gh_78c3a0f83969_258.jpg)

**扫描葵花码体验小程序**

# 1.0版 - 使用教程（不推荐）

**1.0版本的代码撰写思路及API调用思路请见[如何在小程序中使用人脸识别](https://www.techeek.cn/wx-AI-face)这篇文章，推荐阅读，这篇文章详述了具体demo的使用及写代码过程中遇到的一些问题。**

## 服务端

- 请点击[这里查看](1.0/server/readme.md)1.0版本服务器使用教程，项目采用Docker+PHP做服务端，并分享PHP代码。

## 客户端

- 请点击[这里查看](1.0/client/readme.md)1.0版本客户端使用教程。

# 2.0版 - 使用教程（推荐）

2.0版本有较大的更新，腾讯云人脸识别API于2019年1月25日全量更新为了3.0版本，API调用方式及也有较大变化。同时腾讯云联合微信团队共同开发了小程序·云开发这款产品，无需用户搭建服务器，即可轻量撰写相关逻辑代码。为此，更新2.0版本，整体Demo更轻量，无需自行购买搭建服务器，况且小程序·云开发这款产品还在免费阶段，同时腾讯云人脸识别服务每月为各个接口提供 1 万次 的免费调用，很划算。

**2.0版本的撰写思路，我都分享到了个人博客中的[无服务器开发人脸识别小程序](https://www.techeek.cn/wx-wxcloud-AIface)这篇文章中，希望您使用前，好好阅读下，这篇文章将分享我开发过程中的一些思路，如何考虑产品应用性，如何优化逻辑等问题。同时也会分享整个的开发过程，从怎么注册账户到怎么调用API，以及代码是如何一点一点拼接的。大家也可以将这篇文章看为一篇教程，我会从0~1分享整个项目的开发过程。当然，如果你是一名Developer，请直接使用我撰写好的代码，欢迎大家参阅！**

首先，将2.0文件夹`clone`到本地，我们会看到`server`及`client`两个文件夹，具体使用步骤如下。


## 服务端

- 打开`server`文件夹下的`DetectFace`、`AnalyzeFace`、`FaceMerge`文件夹，找到`config.js`文件,将SecretId和SecretKey替换成你在腾讯云注册的ID即可。
```
    SecretId: 'YourSecretId', //腾讯云的YourSecretId，请替换成你自己的
    SecretKey: 'YourSecretKey' //腾讯云的YourSecretKey，请替换成你自己的
```

- 打开`server`文件夹下的`DetectFace`、`AnalyzeFace`、`FaceMerge`文件夹，找到`index.js`文件,将eva替换成你云函数的环境。
```
    cloud.init({
      env: 'YourwxcloudID'
    }) //将YourwxcloudID替换成你自己的云开发环境ID
```

之后上传项目到你的云函数目录即可。

## 客户端
- 打开`client`文件夹下的`pages\index`文件夹，找到`index.js`文件,将eva替换成你云函数的环境。
```
    wx.cloud.init({
      env: 'YourwxcloudID' //将YourwxcloudID替换成你自己的云开发环境ID
    })
```
之后运行测试即可运行。


# 更新日志  
> **2.2** - 2019年2月22日 修复云函数初始化BUG，该BUG会造成后台服务函数无法获取图片临时地址。新增五官定位（人脸识别框及标记）功能。
>
> **2.1** - 2019年1月30日 更新前端，恢复至1.0样式。因为腾讯云API 3.0将人脸检测API和人脸定位API分离，暂未写相关后端，人脸识别框及标记下个版本更新。
>
> **2.0** - 2019年1月28日 重构前后端代码，后端部署方式变更为小程序·云开发（云函数及云存储），人脸识别API更换为腾讯云3.0版本。
>
> **1.4** - 2018年12月17日 修改服务端为Docker服务，部署更加便捷。小程序端代码增加备注  
>
> **1.3** - 2018年12月14日 新增人脸识别框及标记  
>
> **1.2** - 2018年11月29日 修复小程序端遮挡及戴帽子误报BUG  
>
> **1.1** - 2018年11月15日 优化代码，不需要在按照以前的教程查看`signature.php`文件后在修改`index.php`才能使用。现在直接按照上文修改相关内容，就可以使用本demo。 将以前多次有效签名变为单次，签名10s内过期，增加安全性。  
>
> **1.0** - 2018年11月13日 创建项目
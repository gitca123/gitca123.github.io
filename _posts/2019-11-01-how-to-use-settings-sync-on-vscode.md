---
layout: post
title:  "VSCode上设置Settings Sync插件"
date:   2019-11-01 10:35:00 -0000
categories: VS_Code
tags: VS_Code
---





找了很久才找到一个有图解的教程，跟着一步步做了一下，完成了配置。

#### 步骤如下：

##### 1、配置gist

2. 登录GitHub创建一个Gist [传送门在这里](https://github.com/settings/tokens)

3. 点击 Generate new token

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件1.png){:width="600px"}

4.  输入备注，勾选gist，点击生成，即可获得一个令牌。 

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件2.png){:width="600px"}

4. 将此令牌保存到本地（此为**令牌**）

5.  点击头像 - your gists；点击头像边上的+号，创建一个新Gist

6. 分别输入描述、文件名、内容（），点击创建私密gist

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件3.png){:width="600px"}

7. 创建成功后将这个gist的网址最后一段字母保存到本地（此为**仓库ID**）

##### 2、安装srttings sync并配置

1. 在应用商店搜索Settings Sync并安装

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件4.png){:width="600px"}

2.  快捷键`Ctrl+Shift+P` 输入命令 `sync` 

3. 依次点击 **同步：高级选项**  - **编辑本地拓展设置**

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件5.png){:width="600px"}

   

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件6.png){:width="600px"}

4.  输入存到本地的**令牌**，保存更改后关闭

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件7.png){:width="600px"}

5.  进入Settings Sync扩展设置页面

6.  输入保存到本地的**仓库ID**

   ![VSCode上设置Settings Sync插件](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/VSCode上设置Settings Sync插件8.png){:width="600px"}

##### 快捷键

- 上传快捷键 : Shift + Alt + U
- 下载快捷键 : Shift + Alt + D



参考内容：

> [CDSN-诗远][1]    

[1]: https://blog.csdn.net/qq_36848370/article/details/97650711 "CDSN-诗远"
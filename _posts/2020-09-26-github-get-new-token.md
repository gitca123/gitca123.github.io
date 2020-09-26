---
layout: post
title: "更换电脑后在VSCode上同步Settings Sync插件"
date: 2020-09-26 00:00:00 -0000
categories: 
tags: VS_Code

---

[之前做过一期Settings Sync插件设置教程](https://gitca233.github.io/2019/11/01/how-to-use-settings-sync-on-vscode/)，现在需要在家里电脑上也配置一次，但是已经忘记了原始的Token，所以写了一下流程以作备用。

### 获取新的Token

这里要注意一下，更新Token以后原来的电脑也不能同步了。

首先登陆github.com，点击"Settings" 、"Developer settings"、"Personal access tokens" ，选择用于同步的那一条token，然后点击重置。

![](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/%E6%9B%B4%E6%8D%A2%E7%94%B5%E8%84%91%E5%90%8E%E5%9C%A8VSCode%E4%B8%8A%E5%90%8C%E6%AD%A5Settings%20Sync%E6%8F%92%E4%BB%B61.png)



![](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/%E6%9B%B4%E6%8D%A2%E7%94%B5%E8%84%91%E5%90%8E%E5%9C%A8VSCode%E4%B8%8A%E5%90%8C%E6%AD%A5Settings%20Sync%E6%8F%92%E4%BB%B62.png)
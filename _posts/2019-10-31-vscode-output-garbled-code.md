---
layout: post
title:  "VS Code 输出乱码的解决方法"
date:   2019-10-31 10:35:00 -0000
categories: VS_Code
tags: VS_Code
---

乱码问题主要是试运行程序时出现在OUTPUT面板上，终端面板可通过更改编码类型进解决。

#### 我的解决方案

1. 文件-首选项-设置
1. 输入 code runner
1. 找到Code-runner.Run In Terminal选项，并勾选
1. 重启VS Code

>上述方法还能解决试运行代码时，output窗口提示“只读”的问题

#### 网上的一些其他方案

##### 1、增加系统全局变量

以 windows 系统为例，添加系统变量：

    PYTHONIOENCODING=UTF8

详细过程如下：

![windoes7设置环境变量PYTHONIOENCODING=UTF8](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/windoes7设置环境变量PYTHONIOENCODING=UTF8-1.png){:width="600px"}

![windoes7设置环境变量PYTHONIOENCODING=UTF8](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/windoes7设置环境变量PYTHONIOENCODING=UTF8-2.png){:width="600px"}

![windoes7设置环境变量PYTHONIOENCODING=UTF8](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/windoes7设置环境变量PYTHONIOENCODING=UTF8-3.png){:width="600px"}

![windoes7设置环境变量PYTHONIOENCODING=UTF8](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/windoes7设置环境变量PYTHONIOENCODING=UTF8-4.png){:width="600px"}

##### 2、修改 VSC 配置文件

F1 键调出控制台，输入task,选择任务：配置任务运行程序,打开tasks.json文件，**增加**以下信息：

    "options": {
     "env":{
     "PYTHONIOENCODING": "UTF-8"
     }

##### 3、在代码里更改编码

在每个需要中文的 python 文件中添加如下代码：

    import io
    import sys
    
    #改变标准输出的默认编码
    sys.stdout=io.TextIOWrapper(sys.stdout.buffer,encoding='utf8')

使用方法1和方法2需要重启 VS Code。

方法1可以一劳永逸。



参考内容：
> [脚本之家][1]    

[1]: https://www.jb51.net/article/151889.htm "脚本之家"
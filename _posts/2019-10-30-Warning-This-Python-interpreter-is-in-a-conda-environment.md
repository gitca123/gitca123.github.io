---
layout: post
title:  "Python错误：Warning:This Python interpreter is in a conda environment"
date:   2019-10-30 10:35:00 -0000
categories: Python
tags: Python 错误代码
---

今天在公司电脑（虚拟桌面）上尝试使用tushare进行上市公司数据爬取，安装Anaconda后，在命令行输入python提示错误：

    Warning:This Python interpreter is in a conda environment, but the environment has not been activated. Libraries may fail to load. To activate this environment please see https://conda.io/activation

尝试使用网上的方法进行解决:

#### 1、确定当前环境

在命令行运行：

    conda info --envs

在显示的环境列表中，当前环境以星号（*）突出显示。

#### 2、激活环境

在命令行继续输入：

    conda activate myenv

其中，menv为第一步提示的环境名称。
---
layout: post
title: "python内将数组array的第一列转换为列表list"
date: 2020-03-27 00:00:00 -0000
categories: 股票
tags: Python Tushare
---


### python内将数组的第一列转换为列表

获取沪深市场上高分红股票，计算并筛选适合低风险投资的几只。

首先通过tushare获取沪深股市所有股票的代码：

```python
pro = ts.pro_api('f33115a52b4112784c3361264c449548ea2279f82af9c6ca')`

data = pro.query('stock_basic', *exchange*='', *list_status*='L', *fields*='ts_code,symbol,name,area,industry,list_date')
```

得到数据如下：

```python
    ts_code  symbol  name area industry list_date

0     000001.SZ  000001  平安银行   深圳       银行  19910403
1     000002.SZ  000002   万科A   深圳     全国地产  19910129
2     000004.SZ  000004  国农科技   深圳     生物制药  19910114
3     000005.SZ  000005  世纪星源   深圳     环境保护  19901210
4     000006.SZ  000006  深振业A   深圳     区域地产  19920427
...         ...     ...   ...  ...      ...       ...
3795  688388.SH  688388  嘉元科技   广东      元器件  20190722
3796  688389.SH  688389  普门科技   深圳     医疗保健  20191105
3797  688396.SH  688396   华润微   江苏      元器件  20200227
3798  688398.SH  688398  赛特新材   福建     矿物制品  20200211
3799  688399.SH  688399  硕世生物   江苏     医疗保健  20191205
```

这时需要获取数组的第一列作为一个列表，以此作为其他接口的查询条件。我们使用numpy进行转换：

```python
import numpy as np #numpy用于数组的行列转化
ar=np.array(data) #数组行列转化
allCodelist = ar[:,0] #获取data数组的的第一列作为股票代码列，用于数据查询
```



参考内容：
> [百度知道][1]    

[1]: https://zhidao.baidu.com/question/263922941210937085.html "Markdown"
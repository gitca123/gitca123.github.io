---
layout: post
title:  "通过Tushare获取上市公司财务数据"
date:   2019-12-26 16:35:00 -0000
categories: 财务数据
tags: Python Tushare 财务
---


### 通过Tushare获取上市公司财务数据

> Tushare是一个开放、免费的平台，不带任何商业性质和目的。目前已经更新至 [Tushare Pro版](https://tushare.pro/)，数据内容扩大到股票、基金、期货、债券、外汇、行业大数据，同时包括了数字货币行情等区块链数据的全数据品类的金融大数据平台，是一个为各类金融投资和研究人员提供适用的数据和工具。
>



### 一、软件安装

#### 1、运行环境安装

Tushare依托Python、pandas，建议直接安装[Anaconda](https://www.anaconda.com/)，即可包含所需全部内容。

#### 2、Tushare安装

**方式1：**`pip install tushare`，如果安装网络超时可尝试国内pip源，如pip install tushare -i https://pypi.tuna.tsinghua.edu.cn/simple 

**方式2：**访问https://pypi.python.org/pypi/tushare/下载安装 ，执行 `python setup.py install`

**方式3：**访问https://github.com/waditu/tushare,将项目下载或者clone到本地，进入到项目的目录下，执行： `python setup.py install`



1. 所有产品都是推荐者自身使用过的。
2. 每个类别工具按照推荐度进行排序。
3. 每个类别工具的数量原则不超过5个。

### 二、获取Token及积分说明

[注册用户](https://tushare.pro/register?reg=317320)即可获得Tushare的Token，进而通过平台爬取数据。

![power query中使用参照表动态替换文章标题](https://raw.githubusercontent.com/gitca233/gitca233.github.io/master/assets/imgs/article/获取Token.png){:width="600px"}

注册帐号后会直接获得100积分，绑定手机、填写单位信息可获得额外20分，[不同积分等级对应不同数据抓取权限](https://tushare.pro/document/1?doc_id=108)，高校学生认证、金融机构从业人员认证可快速获得积分。金融机构从业人员可直接获得2000积分，除爬取频次外，和5000积分会员效果无异。

### 三、接口介绍

对于财务数据，Tushare提供了以下接口：

首先需要导入Token

```python
pro = ts.pro_api(xxxxxx)
```

#### 1、利润表

```python
df = pro.income_vip(period='20191231',fields='ts_code,ann_date,f_ann_date,end_date,report_type,comp_type,basic_eps,diluted_eps')
```

#### 2、资产负债表

```python
df = pro.balancesheet_vip(period='20191231',fields='ts_code,ann_date,f_ann_date,end_date,report_type,comp_type,cap_rese')
```

#### 3、现金流量表

```python
df = pro.cashflow_vip(period='20191231',fields='')
```

#### 4、财务指标数据

```python
df = pro.query('fina_indicator', ts_code='600000.SH', start_date='20190101', end_date='20191231')
```

#### 5、主营业务构成

```python
df = pro.fina_mainbz_vip(period='20191231', type='P' ,fields='ts_code,end_date,bz_item,bz_sales')
```

### 四、参考代码

```python
# -\- coding: utf-8 -\-

import os
import tushare as ts #调用tushare接口*
import time

#输入key
pro = ts.pro_api('f33115a58b4cec43b03718654c3361264c449548ea2819f82af9c6ca')

allCodelist=['600998.SH'#以九州通举例]

time1 = '20150101'
time2 = '20191231'

for code in allCodelist:

  print('正在获取证券%s数据 ...' % code)

  df = pro.fina_mainbz( ts_code =code, start_date  = time1,  end_date  = time2,  type  ='D')#通过接口获取数据
  df.to_csv('d:\\财务报告\\主营业务构成_地区\\' + '主营业务构成_地区_' + code + '.csv', encoding  = 'utf-8') #保存到D盘“财务报告”文件夹的“主营业务构成_地区”文件夹内
```


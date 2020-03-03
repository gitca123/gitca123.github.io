---
layout: post
title:  "破解VAB工程密码"
date:   2019-11-19 10:35:00 -0000
categories: OFFICE
tags: Excel VBA
---


### 一、Excel工程锁定

#### 1、共用级锁定
1. 先对excel档进行一般的vbaproject”工程密码保护。
2. 打开要保护的档，选择∶工具--->保护--->保护并共用活页簿--->以追踪修订方式共用-->输入密码-->保存档。 完成後，当你打开“vbaproject”工程属性时，就将会提示∶“工程不可看！”

#### 1、破坏型锁定（推荐）
1. 用16进制编辑工具，如winhex、ultraedit-32（可到此下载）等，再历害点的人完全可以用debug命令来做......用以上软件打开excel档，查找定位以下地方∶
2. id="{00000000-0000-0000-0000-000000000000}" 注∶实际显示不会全部为0
3. 此时，你只要将其中的位元组随便修改一下即可。保存再打开，就会发现大功告成！
4. 当然，在修改前最好做好你的文档备份。至於恢复只要将改动过的地方还原即可。


### 二、Excel工程解锁
破解方面,有网友说将CMG=，DPB=和GC=后的"="替换为"."也可以的，我已测试过的确可以，这样更省事点。用16进制编辑工具，如winhex、ultraedit-32打开X.xls文件，查找ID=......, 或到文件尾查看，找到即可。

改其中的任意一位,存盘就可达到目的，注意：留有备份文件

#### 1、hex editor破解VABProject密码

1. 下载hex editor二进制编辑器,使用查找功能定位到DPB=”…….上。
2. 把DPB更改成DPx保存
3. 重新打开EXCEL会提示错误未找到关键字DPx是否继续加载工程，选择“是”
4. 按Alt+F11打开VBA工程，右键顶节点，VBAProject属性，保护，重新输入一个新密码，保存excel
5. 再次打开就可以用新密码解锁VBA工程

[64位Notepad++的HexEditor下载](https://github.com/chcg/NPP_HexEdit/releases)

[HexEditor客户端下载](http://www.chmaas.handshake.de/delphi/freeware/xvi32/xvi32.htm#download)

#### 2、通过宏进行VBA工程密码破解

在办公中我们常看到许多用宏(VBA)编写的EXCEL表格,而这些表格就如同一个数据库,我们可以选取或查询很多的数据,一般的这些数据是存放在一个隐藏的工作表中的,那么要如何显示这个隐藏的工作表呢?我们可以打开宏编辑器(ALT+F11),再安CTRL+R打开专案,这时弹出窗会有所有的这个EXCEL的工用表,这时你就可以看看那些是被隐藏的了,很多时候打开是需要密码的,用以下方法解密后,再将解密后文件打开,依同样方法在工作表标签中右键>>检视程式码>>复制以下代码>>按F8执行

    Private Sub CommandButton1_Click()
    Worksheets("这里为你要显示的工作表名称").Visible = True
    End Sub

关于破解EXCEL VBA工程密码的方法,以下代码非常有效,首先建一新EXCEL文件,在工作表标签处右点>>检视程式码>>复制以下代码>>按F8执行 在弹出窗中选你要你破解工程密码的EXCEL文件 >>再按F5执行即可.

    Private Sub VBAPassword()
    '你要解保护的Excel文件路径
    Filename = Application.GetOpenFilename("Excel文件（*.xls & *.xla & *.xlt）,*.xls;*.xla;*.xlt", , "VBA破解")
    If Dir(Filename) = "" Then
    MsgBox "没找到相关文件,清重新设置。"
    Exit Sub
    Else
    FileCopy Filename, Filename & ".bak" '备份文件。
    End If
    
    Dim GetData As String * 5
    Open Filename For Binary As #1
    Dim CMGs As Long
    Dim DPBo As Long
    For i = 1 To LOF(1)
    Get #1, i, GetData
    If GetData = "CMG=""" Then CMGs = i
    If GetData = "[Host" Then DPBo = i - 2: Exit For
    Next
    
    If CMGs = 0 Then
    MsgBox "请先对VBA编码设置一个保护密码...", 32, "提示"
    Exit Sub
    End If
    
    If Protect = False Then
    Dim St As String * 2
    Dim s20 As String * 1
    
    '取得一个0D0A十六进制字串
    Get #1, CMGs - 2, St
    
    '取得一个20十六制字串
    Get #1, DPBo + 16, s20
    
    '替换加密部份机码
    For i = CMGs To DPBo Step 2
    Put #1, i, St
    Next
    
    '加入不配对符号
    If (DPBo - CMGs) Mod 2 <> 0 Then
    Put #1, DPBo + 1, s20
    End If
    MsgBox "文件解密成功......", 32, "提示"
    End If
    Close #1
    End Sub
    
    如果上面代码不能运行或出错,请用以下代码重试.
    
    Private Sub VBAPassword()
    '你要解保护的Excel文件路径
    Filename = Application.GetOpenFilename("Excel文件（*.xls & *.xla & *.xlt）,*.xls;*.xla;*.xlt", , "VBA破解")
    
    If Dir(Filename) = "" Then
    MsgBox "没找到相关文件,清重新设置。"
    Exit Sub
    Else
    FileCopy Filename, Filename & ".bak" '备份文件。
    End If
    
    Dim GetData As String * 5
    Open Filename For Binary As #1
    Dim CMGs As Long
    Dim DPBo As Long
    For i = 1 To LOF(1)
    Get #1, i, GetData
    If GetData = "CMG=""" Then CMGs = i
    If GetData = "[Host" Then DPBo = i - 2: Exit For
    Next
    
    If CMGs = 0 Then
    MsgBox "请先对VBA编码设置一个保护密码...", 32, "提示"
    Exit Sub
    End If
    
    Dim St As String * 2
    Dim s20 As String * 1
    
    '取得一个0D0A十六进制字串
    Get #1, CMGs - 2, St
    
    '取得一个20十六制字串
    Get #1, DPBo + 16, s20
    
    '替换加密部份机码
    For i = CMGs To DPBo Step 2
    Put #1, i, St
    Next
    
    '加入不配对符号
    If (DPBo - CMGs) Mod 2 <> 0 Then
    Put #1, DPBo + 1, s20
    End If
    MsgBox "文件解密成功......", 32, "提示"
    
    Close #1
    End Sub



参考内容：

> [ncgege][1]    

[1]: https://blog.csdn.net/esonbest1234/article/details/50729515 "CDSN"
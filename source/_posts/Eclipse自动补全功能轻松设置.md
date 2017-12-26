---
title: Eclipse自动补全功能轻松设置
date: 2017-11-24 12:53:12
tags: Eclipse自动补全
categories: Eclipse
---
#### Eclipse代码自动补全功能默认只包括 点”.” ，即只有输入”.”后才出现自动补全的提示框。  
#### 想要自动补全总是去按 “Alt + / ”也很麻烦。 
#### 其实只需简单在Eclipse中进行设置即可实现输入任意及符合自动出现自动补全提示框。

### 具体设置步骤如下：　　
#### 1.选择Eclipse菜单条中的Windows菜单下的Preferences项　

#### 2.在左侧找到“Java” -> “Editor” -> “Content Assist”（鼠标点击此项） 
#### 3.在右侧“Auto Activation”项目下找到“Auto activation triggers for Java:”（可以看到设置框中默认的只有 “.” ，这就是为什么默认只有点“.” 可以触发自动补全窗口了) 
#### 4.在框中点”.”后输入你想要的触发自动补全的字母（中间不需要隔开，挨着依次键入即可），如：“abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ.”，这样写代码时输入任意的大小写字母均会触发自动补全窗口弹出 
#### 5.输入完后确定OK即可。

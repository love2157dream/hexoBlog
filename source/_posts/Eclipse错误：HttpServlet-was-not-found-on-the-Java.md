---
title: Eclipse错误：HttpServlet was not found on the Java
date: 2017-11-24 12:28:24
tags: 
    - error
    - Eclipse
categories: Eclipse
---
# 我们在用Eclipse进行Java web开发时，可能会出现这样的错误：The superclass javax.servlet.http.HttpServlet was not found on the Java Build Path。

### 1.我们遇到的错误显示如下：
![](Eclipse错误：HttpServlet-was-not-found-on-the-Java/9.jpg)

### 2.我们右击有错误提示的文件夹，如下： 
![](Eclipse错误：HttpServlet-was-not-found-on-the-Java/10.jpg)

### 3.我们点击”配置构建路径“，如下： 
![](Eclipse错误：HttpServlet-was-not-found-on-the-Java/11.jpg)

### 4.我们再点击”添加库“，如下 
![](Eclipse错误：HttpServlet-was-not-found-on-the-Java/12.jpg)

### 5.我们选中上图中标出的选项，再点击下一步，如下： 
![](Eclipse错误：HttpServlet-was-not-found-on-the-Java/13.jpg)


### 6.我们再点击”完成“，如下： 
![](Eclipse错误：HttpServlet-was-not-found-on-the-Java/14.jpg)

### 7.我们再点击”正常“，即可完成设置。这样我的错误就会消失了，如下: 
![](Eclipse错误：HttpServlet-was-not-found-on-the-Java/15.jpg)
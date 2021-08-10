---
title: opencv-python版本不同的环境配置
date: 2020-07-29 11:53:28
cover: ../img/c5.png
tags:
---
因为(py27)是安装的别人发的安装包，可能是版本没更新，用pip管理的时候就报错**Fatal error in launcher: Unable to create process using**
解决方法：升级pip
**python -m pip install -U pip**
successfully则成功升级

我运行一个文件（a），用这个py27环境刚刚好
后来有一个文件(b)运行，要求opencv版本为3.1.0，版本不对，然后不停的报错
解决：**pip install opencv-python==3.1.0**
emm,那个文件(b)成功运行了，不过！！！我的文件a成功报错了，想哭，我又要重新配置
解决方法：
1. 克隆环境（py27）为（py27_1）
**conda create --name py27_1 --clone py27**
制作py27环境的克隆,名字为py27_1
原因：保住文件b可以运行，以后它运行的时候就切换成py27_1的环境
2. 在py27环境中 **pip install opencv-python**，如果还是不行并且你没有记住之前文件（a）运行对应的opencv的版本号，那就
先删除py27环境，**conda remove -n py27 --all**
然后重新下载别人给你发的安装包，切换环境，ok，完成

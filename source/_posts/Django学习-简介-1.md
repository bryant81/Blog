---
title: Django学习-简介(1)
date: 2018-01-03 10:00:29
tags:
    - django
    - python 
categories: Django
---

![django](django.jpeg)

# 为什么是Django?

使用Django，你可以把更多的精力放在写业务关系，而不是通过造轮子来开发很多网页服务实现的细节，而且是__免费__和__开源__的

<!--more-->

## 开发特别快

使用Django可以让你更快的把概念形成具体的网页产品，只需要简单的几步

## 工具特别全

Django包含了很多模块用于快速完成网页开发任务，比如认证系统，内容管理，网站地图，RSS等

## 令人感到安全

Django对于安全处理非常靠谱，可以帮你处理绝大多数安全问题，比如SQL注入，跨站脚本攻击，跨站请求伪造以及点击劫持, 它的用户认证系统可以提供一个安全方式来管理用户的账号和密码。

## 分布式支持

对于访问量很大需求，Django提供了分布式支持，可以尽可能的充分利用管理人员提供的硬件资源

## 应对各种场景
公司/机构/政府需要的网页服务都可以使用Django来搭建，从内容管理系统到社会网络以及科学计算平台，满足各种需求

# 安装Django

## 安装环境

* MacbookPro High Sierra / Darwin Kernel Version 17.3.0

## Python

* Python 3.6.1 「由于我们计划安装Django 2.1，按照官方要求需要Python3.5+」

## 数据库

Django支持很多数据库引擎，比如PostgreSQL/MySQL/Oracle, 这些都是比较大型的数据库，我们为了简单用的是自带的轻量级数据库-SQLite, 就不需要额外安装了

## 卸载旧的Django版本

* 如果使用的是pip/easy_install进行安装的旧库，可以直接使用pip/easy_install来直接安装，对于旧的库安装程序会自动处理
* 如果是手动通过python setup.py install安装的旧库，直接删除掉在site-packegs里的django目录就可以了，可以通过下面的命令找到目录所在位置
> $ python -c "import django; print(django.__path__)"

## 安装新的Django版本

有以下三种版本选择：

* 通过pip安装官方发布的正式的版本
> $ pip3 install Django==2.0.1

* 通过操作系统发型的版本安装
* 通过下载源码来安装最新的版本，这个是对于那些急于获取新特性但又不担心遇见bug的粉丝们使用

## 验证安装
> $ python3 -c "import django; print(django.get_version())"
> $ 2.0.1

---
title: Ubuntu16.04LTS下搭建Gitlab
date: 2018-03-28 16:47:51
tags:
    - gitlab
    - git

categories: 软件管理
toc: true
---


# 在Ubuntu16.04-LTS下安装Gitlab

Git的好处无须多说，分布式，快速分支，更清晰的开发流程等等，所以计划把公司的代码从SVN转移到Git，在使用了GitHub和Gitlab两个网站后，决定自己在公司的局域网内搭建Gitlab.

<!--more-->

## 安装Ubuntu16.04-LTS

* 下载：推荐安装amd64版本 [种子](http://releases.ubuntu.com/16.04/ubuntu-16.04.4-desktop-amd64.iso.torrent?_ga=2.16967225.1283571371.1522211051-1536568839.1517620741) 
* 安装：我是用VMWare11安装的，主力需要注意将DDR调整为4GB，这个是Gitlab官方推荐的大小
* 更新源: 我这里使用的是清华镜像，速度很快。gitlab-ce也会用到清华的镜像，后面会提到
> vi /etc/apt/source.list
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security multiverse

* 更新软件仓库
> sudo apt-get update

## 安装Gitlab相关

* 安装ssh服务和认证服务
> sudo apt-get install -y curl openssh-server ca-certificates 

* 安装邮件服务,如果不需要邮件通知或者使用其他的邮件服务，比如sendmail等可以跳过
> sudo apt-get install postfix

* 信任 GitLab 的 GPG 公钥
> curl https://packages.gitlab.com/gpg.key 2> /dev/null | sudo apt-key add - &>/dev/null

* 将下列源手动添加到/etc/apt/sources.list.d/gitlab-ce.list文件中，如果没有手动创建
> deb https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/ubuntu xenial main

* 安装gitlab-ce
> sudo apt-get update
> sudo apt-get install gitlab-ce

## 配置Gitlab相关

* 设置LC_ALL LC_CTYPE: 如果不设置，在gitlab-ctl reconfigure的时候会报LC_ALL相关的错
> vi ~/.bashrc
> export LC_ALL="en_US.UTF-8"
> export LC_CTYPE="en_US.UTF-8"

* 设置访问路径
> vi /etc/gitlab/gitlab.rb
> external_url 修改为你给定的访问路径，我设置的为 "http://192.168.41.8:8866", 仅限局域网访问

* 重新生成配置
> sudo gitlab-ctl reconfigure

* 重启服务
> sudo gitlabl-ctl restart

## 第一次访问

* 直接使用external_url的地址可以访问到gitlab提供的网站服务
* 默认用户名是root,第一次访问会强制让你修改密码

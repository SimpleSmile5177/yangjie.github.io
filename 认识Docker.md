---
title: 认识Docker
date: 2018-08-20 14:32:00
toc: true
tags:
---

# 什么是Docker  
&nbsp;&nbsp;&nbsp;Docker是基于Go语言实现的开源容器项目，诞生于2013年年初，最初发起者是dotCloud公司。Docker自开源后受到广泛的关注和讨论，目前已有多个相关项目（包括Docker三剑客、Kubernetes等），逐渐形成了围绕Docker容器的生态体系。  

<!more/>
&nbsp;&nbsp;&nbsp;现如今，主流的linux操作系统都已经支持Docker（Redhat，CentOS，Ubuntu，在更高本中，都已经安装了Docker）。  
# Docker有什么用  
&nbsp;&nbsp;&nbsp;打个比方，比如有一套SSM（Spring,springMVC,Mybatis）架构的系统,有一天我们想移植这个项目，放到哪个服务器或者云服务上面，我们就必须还得先在服务器上搭建一套跟之前一样的环境。例如安装jdk，tomcat的配置，和其他繁琐的配置。这个不尽降低了工作效率，还很容易出现问题。 
&nbsp;&nbsp;&nbsp;而Docker它是通过容器来打包应用。迁移的时候只需要在新的服务器上启动需要的容器即可。无论新旧平台是否一样，这就可以节约大量的时间，还降低了迁移时出错的概率。  
&nbsp;&nbsp;&nbsp;Docker容器对系统资源需求很少，一台主机上可以同时运行数千个Docker容器。  
# CentOS 安装Docker  
Docker 支持 CentOS6 及以后的版本。  
### CentOS6  
对于 CentOS6，可以使用 EPEL 库安装 Docker，命令如下  
```  
$ sudo yum install http://mirrors.yun-idc.com/epel/6/i386/epel-release-6-8.noarch.rpm  
$ sudo yum install docker-io  
```  
### CentOS7 
CentOS7 系统 CentOS-Extras 库中已带 Docker，可以直接安装：  
`$ sudo yum install docker`  
安装之后启动 Docker 服务，并让它随系统启动自动加载。  
```
$ sudo service docker start
$ sudo chkconfig docker on  
``` 

# 未完待续。。。

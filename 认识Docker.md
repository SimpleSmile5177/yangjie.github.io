---
title: 认识Docker
date: 2018-08-20 14:32:00
toc: true
tags: Docker
---

# 什么是Docker  
&nbsp;&nbsp;&nbsp;Docker是基于Go语言实现的开源容器项目，诞生于2013年年初，最初发起者是dotCloud公司。Docker自开源后受到广泛的关注和讨论，目前已有多个相关项目（包括Docker三剑客、Kubernetes等），逐渐形成了围绕Docker容器的生态体系。  

<!--more-->
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
```  
$ sudo yum install docker  
```

安装之后启动 Docker 服务，并让它随系统启动自动加载。  
```  
$ sudo service docker start  
$ sudo chkconfig docker on  
```
  
# Docker的基本概念  
### 镜像（Image）  
### 容器（Container）  
### 仓库（Repository）  
理解了这三个概念，就理解了 Docker 的整个生命周期。  
## Docker镜像  
&nbsp;&nbsp;&nbsp;**镜像，从认识上简单的来说，就是面向对象中的类，相当于一个模板。**从本质上来说，镜像相当于一个文件系统。Docker 镜像是一个特殊的文件系统，除了提供容器运行时所需的程序、库、资源、配置等文件外，还包含了一些为运行时准备的一些配置参数（如匿名卷、环境变量、用户等）。镜像不包含任何动态数据，其内容在构建之后也不会被改变。  
## Docker容器  
&nbsp;&nbsp;&nbsp;**容器，从认识上来说，就是类创建的实例，就是依据镜像这个模板创建出来的实体。**容器的实质是进程，但与直接在宿主执行的进程不同，容器进程运行于属于自己的独立的命名空间。因此容器可以拥有自己的root 文件系统、自己的网络配置、自己的进程空间，甚至自己的用户ID 空间。容器内的进程是运行在一个隔离的环境里，使用起来，就好像是在一个独立于宿主的系统下操作一样。这种特性使得容器封装的应用比直接在宿主运行更加安全。  
## Docker仓库  
&nbsp;&nbsp;&nbsp;**仓库，从认识上来说，就好像软件包上传下载站，有各种软件的不同版本被上传供用户下载。**镜像构建完成后，可以很容易的在当前宿主机上运行，但是，如果需要在其它服务器上使用这个镜像，我们就需要一个集中的存储、分发镜像的服务，Docker Registry 就是这样的服务。  
国内也有一些云服务商提供类似于 Docker Hub 的公开服务。比如 时速云镜像仓库、网易云镜像服务、DaoCloud 镜像市场、阿里云镜像库。  

## 福利  
[我这里有关于学习Docker的数据，分享给大家。](https://pan.baidu.com/s/1p5FSYkyI6orWqK0txh3Itw)密码：88c9
# 未完待续。。。

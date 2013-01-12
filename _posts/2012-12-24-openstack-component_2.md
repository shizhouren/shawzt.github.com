---
layout: post
title: "OpenStack组件说明之二"
description: "OpenStack组件——Glance、Keystone、Horizon简介"
categories: [云计算]
tags: [OpenStack]
---

__3. 镜像服务——Glance__  
Glance是OpenStack中的一个虚拟机镜像的存储、注册、查询和检索的系统。Glance被设计成可以使用多种后端存储的方式，其目前支持的镜像存储方式有：本地文件系统；Swift；S3；Http只读存储。Glance的设计方式遵循以下思想：基于组件的架构——便于快速增加新特性；高可用性——支持大负荷；容错性——独立进程避免串行错误；开放标准——提供社区API参考实现。 Glance的结构如下图所示：![Glance结构](/assets/images/Glance_architecture.png)   
__4. 认证服务——Keystone__  
Keystone为所有的OpenStack组件提供认证和访问策略服务。它依赖自身基于Identity API的REST系统进行工作，主要对Swift、Glance、Nova等进行认证与授权。Keystone的认证管理过程见下图：  
![Keystone认证管理](/assets/images/keystone.png)  
Keystone采用基于用户名/密码和基于令牌的两种授权方式，并提供以下三种服务：令牌服务、目录服务和策略服务。在提供认证和授权服务过程中，涉及以下概念：  

* 服务  
		任何通过Keystone进行连接或管理的组件，如Glance就是Keystone的服务。  
* 服务入口  
		指定的端口和专属URL，每个OpenStack均拥有唯一的一个服务入口。  
* 角色  
		为维护云安全而设定的权限分组。  
* 用户  
		Keystone授权使用者。

__5. 管理接口——Horizon__  
Horizon是一个模块化的Django Web应用程序，为终端用户和系统管理员提供界面来管理OpenStack服务。它可以控制实例、管理镜像、创建密钥对、操作卷及Swift容器等，同时用户可以在Horizon中使用终端直接访问实例。界面下图。  
![OpenStack控制面板](/assets/images/horizon_web.png)   

备注：组件之间的交互见<a target="blank" href="/blog/12-21-2012/openstack_review/#component">交互图</a>

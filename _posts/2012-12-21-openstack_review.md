---
layout: post
title: "OpenStack架构简介"
description: "云计算包括三大服务：基础设施即服务（IaaS）；软件即服务（SaaS）；平台即服务（PaaS），而OpenStack正是IaaS系列中的优秀者。它是一套开源软件项目的综合体，使得任何人都可以自行建立、部署云平台并提供云计算服务。本文简要介绍OpenStack的架构"
category: [云计算]
tags: [云计算,IaaS,OpenStack]
---
云计算的相关概念介绍见我的
<a target="blank" href="/blog/12-19-2012/cloud_computing/">云计算——简介</a>	
OpenStack是一个由美国国家航空航天局（NASA）和托管服务提供商Rackspace合作开发的，以Apache许可证授权的自由软件和开源项目。作为IaaS层次软件，OpenStack由几个重要组件构成，旨在为企业或个人提供建设和管理公用及私有云的软件。	

####__OpenStack技术支持__
* 使用Python语言编写	
* 整合Tornado网页服务器	
* Nebula运算平台	
* 使用Twisted软件框架	
* 遵循Open Virtualization Format、AMQP、SQLAlchemy等标准	
* 支持KVM、Xen、VirtualBox、VMware、LXC等虚拟机软件。	

####__OpenStack企业支持__
* 硬件厂商有AMD、Intel、惠普以及戴尔等  
* 微软将在Windows Server R2中与OpenStack整合  
* Ubuntu在11.04版本中加入了OpenStack  
* 思科在2011年2月加盟OpenStack项目，重点研制OpenStack的网络服务
<pre>新浪、华为及相关高校也参与研究、积极宣传，共同创建了公益性的OpenStack体验、测试和开发
平台——<a target="blank" href="http://stacklab.org/">Stack Lab</a>实验室，促进OpenStack在国内的普及。在众多企业和高校的加盟和支持，营造了
一个良好的OpenStack社区，进一步推动了OpenStack的发展。</pre>

####__OpenStack基本架构__
OpenStack包括一组由社区维护的开源项目，主要有提供计算服务的Nova、提供存储服务的Swift、提供镜像服务的Glance、提供认证服务的Keystone以及提供UI服务的Horizon。OpenStack的基本架构见下左图所示，组件之间的交互见下右图。		
![OpenStack基本架构](/assets/images/OpenStack_architecture.png)
![OpenStack组件交互](/assets/images/OpenStack_communication1.png)  

<h5 id="component">OpenStack组件交互图</h5>
![OpenStack组件交互](/assets/images/openstack_communication2.png) 
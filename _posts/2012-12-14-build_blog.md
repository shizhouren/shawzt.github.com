---
layout: post
title: "利用Jekyll+Git+GitHub组合，创建自己的博客"
description: "本文结合自己的实践，介绍如何利用Jekyll+Git+GitHub组合，创建一个真正属于自己的博客。该博客的搭建和使用需要一定的技术基础。"
category: 杂集
tags: [折腾]
---

###**导言**
很多人都有写博客的冲动，可是只有很少一部分的人会坚持着。究其原因，可能有很多。但是我个人觉得大多数都是因为没有找到一个真正属于自己的博客：要么是有植入性的广告、要么是简陋的设计、要么是繁琐的操作。。。反正就是没法让人满意，我们没法真正地控制自己的博客：我要设计自己的页面、我要创建自己的分类、我要添加自己的插件。。。  
现在，这些烦恼都可以抹去了。利用Jekyll+Git+GitHub组合，可以创建一个托管的却可以自己控制的博客了。你现在你访问的博客，就是使用上述组合实现的。下面，我就根据一些教程并结合自己的实践，整理出利用上述组合搭建博客的步骤及注意点。
###**实践**
__*一.创建GitHub账户及项目库*__  

	1. 访问[GitHub]:<https://github.com/>，并根据要求创建账户(已有账户则跳过)，见图1；
	2. 登录GitHub后，创建一个Repository：UserName.github.com，
		(注意：UserName替换成你在GitHub上的用户名)，见图2；
	3. 该阶段工作完成！
图1：  
![注册GitHub账号](/assets/images/github.png)  
图2：  
![添加SSH Key](/assets/images/createRepo.png)  
__*二.Git客户端安装及其配置*__

	1. 在Linux系统上，可以使用apt-get install git-core安装；
	2. 主要介绍Windows系统下的安装和配置，我使用的是MsysGit；
	3. MsysGit可从这里下载：<http://code.google.com/p/msysgit/downloads/list>；
	4. 根据安装向导，Next-->Next-->……-->Finish；
	5. 相关配置，打开Git Bash(注意：该控制台对中文支持不好!)：
		5.1 生成SSH Key：输入ssh-keygen -C "你的email地址" -t rsa;
		5.2 提示生成rsa密钥对，选择密钥文件保存位置(默认即可)及加密串
			(警告:该加密串将是你以后提交时的密码。若无需密码，回车即可)；
		5.3 密钥生成。接下来是将公钥信息添加到GitHub上，用于SSH链接；
		5.4 用文本编辑工具打开刚保存的id_rsa.pub文件(可能会被隐藏),做如下操作：
			Ctrl+A-->Ctrl+C-->登录GitHub-->点击右上角的Account Settings-->
			点击左侧SSH Keys-->点击右侧Add SSH Key-->输入该密钥的标识名(Title)-->
			在Key对应的文本域中Ctrl+V，将上述文件中的信息粘贴进去-->点击Add Key保存；
		5.5 在Git Bash中，输入ssh -T git@github.com，出现提示，输入 yes后将会看到
			授权链接成功的信息；
		5.6 以上步骤已基本配置好Git客户端和GitHub的链接；接下来完善使用配置；
		5.7 在Git Bash中，输入git config --global user.name "你的名字"；
		5.8 在Git Bash中，输入git config --global user.email "你的email"；
		5.9 以上两条配置是用于GitHub的权限处理以及Git对提交信息的记录，基本配置完成。
__*三.安装依赖软件*__

	1. 安装Ruby：<http://rubyinstaller.org/downloads/>，在RubyInstallers下选择；
	2. 安装DevKit：<http://rubyinstaller.org/downloads/>，在Development Kit下选择；
	3. 安装Jekyll：在Git Bash中，输入gem install jekyll或者sudo gem install jekyll；
	4. 安装MarkDown语言的解析器：在Git Bash中，输入gem install rdiscount kramdown；
__*四.创建博客*__

	1. 在Git Bash中，输入如下命令：
		git clone https://github.com/plusjade/jekyll-bootstrap.git 目标位置
		该命令是将GitHub上jekyll-bootstrap项目克隆至本机的目标位置(建议以英文命名)；
	2. cd 目标位置 (说明：目标位置将是你的博客在本机的副本)；
	3. git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
		(说明：USERNAME是你在GitHub上的用户名，USERNAME.github.com将是你的博客地址)；
	4. git pull;
	5. git push origin master;
	6. 博客已创建好，接下来的工作就是学习该组合相关知识，弄懂博客结构，然后就坚持写作吧！
	7. 小贴士：在Git Bash中，输入如下命令：
		export LC_ALL=en_US.UTF-8
		export LANG=en_US.UTF-8
		以上两条命名，是为了解决本机中文博客无法预览的问题，但是若不想每次启动Git Bash时
		都输入上述命令，则可以采用以下方法：添加两对用户自定义的环境变量
		LC_ALL=en_US.UTF-8和LANG=en_US.UTF-8
		(提示：Windows-->环境变量)
		cd目标位置；输入 jekyll --server
		在浏览器中输入http://localhost:4000/可以预览你的博客了O(∩_∩)O~
###**资料**
<h4 id="Git">No1. Git</h4>
	1. <http://rogerdudler.github.com/git-guide/index.zh.html>
	2. <http://git-scm.com/>
	3. <https://github.com/progit/progit>
	4. <https://github.com/blynn/gitmagic>
####No2. GitHub
	1. <https://github.com>
	2. <https://help.github.com/>
	3. <https://github.com/blog>
####No3. Jekyll
	1. <http://jekyllbootstrap.com/>
####No4. Liquid
	1. <https://github.com/Shopify/liquid/wiki>
####No5. MarkDown
	1. <http://wowubuntu.com/markdown/index.html>
---
layout: post
title: "Ubuntu12.04 个性化配置"
description: "Ubuntu是适合Linux初学者的系统。学习Linux就要敢于尝试，敢于实践。本文是自己在使用Ubuntu过程中的一些捣鼓，备忘一下。"
category: 技术
tags: [Linux]
---
###__启动引导界面__	
__1. 去除memtest选项__	

	cd /etc/grub.d                                      #进入grub执行脚本目录
	ls                                                         #查看所有脚本列表，存在20_memtest86+脚本
	sudo chmod -x 20_memtest86+         #取消该脚本的可执行权限
	sudo update-grub                               #更新/boot/grub/grub.cfg文件
	#重新启动即可

__2. 去除恢复模式选项__

	sudo vim /etc/default/grub               #查看grub的配置文件
	#将GRUB_DISABLE_RECOVERY="true"之前的#删除
	#保存退出
	sudo update-grub                             #更新/boot/grub/grub.cfg文件
	#重新启动即可

__3. 修改等待时间__

	sudo vim /etc/default/grub              #查看grub的配置文件
	#修改GRUB_TIMEOUT=后的数值
	#保存退出
	sudo update-grub                            #更新/boot/grub/grub.cfg文件
	#重新启动即可

__4. 修改启动项的显示顺序__

	cd /etc/grub.d                               #进入grub执行脚本目录
	ls                                                  #查看所有脚本列表，存在许多以数字开头的脚本
	#其中10_linux是当前linux系统的启动脚本;30_os-prober是其他系统的引导脚本
	#双系统下只需将30_os-prober文件重命名成**_os-prober，**小于10即可
	#其他系统将显示在启动列表的前面
	#保存退出
	sudo update-grub                         #更新/boot/grub/grub.cfg文件
	#重新启动即可

__5. 修改启动项的名字__

	cd /etc/grub.d                              #进入grub执行脚本目录
	ls                                                 #查看所有脚本列表，存在20_memtest86+脚本
	sudo vim 10_linux                       #查看linux系统的引导脚本
	#找到printf "menuentry '×××××××'，将×××××××修改成你想要的Linux系统名字
	#保存退出
	sudo vim 30_os-prober               #查看其他系统的引导脚本
	#找到menuentry "×××××" --class windows，将×××××修改成你想要的Windows系统名字
	#保存退出
	sudo update-grub                        #更新/boot/grub/grub.cfg文件
	#重新启动即可

__6. 修改启动引导背景图片__

	sudo vim /etc/default/grub         #查看grub的配置文件
	#修改GRUB_GFXMODE=后的数字为你屏幕的分辨率
	#删除前面的#，保存退出
	#将你需要的适配分辨率的图片拷贝到/boot/grub目录下
	sudo update-grub                       #更新/boot/grub/grub.cfg文件
	#重新启动即可
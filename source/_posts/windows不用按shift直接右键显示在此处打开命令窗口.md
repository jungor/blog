title: "windows不用按shift直接右键显示'在此处打开命令窗口'"
date: 2015-08-04 16:32:44
tags: windows
---
正常情况，直接右键文件夹图标或者右键文件夹里面空白处，右键菜单都没有“在此处打开命令窗口”；
想要有下图的效果，就必须要这样：按住shift键的同时右键

![](http://hi.csdn.net/attachment/201005/13/182049_1273714360GQ59.png)


然而，虽然不得不承认windows是很渣的开发环境，然而作为一个IT（ma）人士(nong)，快速地打开命令窗口还是很nice的
下面就介绍如何通过修改注册表来实现不需要按住shift键，直接右键就可以在菜单中显示“在此处打开命令窗口”。
本人历经win7/8/8.1/10（明明就是windows粉还好意思黑windows=。=），方法都行得通，而且并无发现副作用

首先打开注册表：win+r，输入regedit，回车确定
![](/images/150804a.png)

实现在我的电脑界面右键驱动器图标（C盘/D盘...）可以显示，把
`HKEY_CLASSES_ROOT/Drive/shell/cmd`
分支的Extended键值删除
![](/images/150804b.png)

同理，实现右键文件夹图标右键文件夹里面空白处，分别把
`HKEY_CLASSES_ROOT/Directory/shell/cmd`
`HKEY_CLASSES_ROOT/Directory/background/shell/cmd`
分支的Extended键值删除即可

至此完成，简单方便。
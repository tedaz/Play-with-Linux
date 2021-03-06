Play-with-Linux
===============
1.1 为什么写这些文字？

作为学习笔记，为了记录在Hyper-V上玩Linux的点点滴滴。

很多信息都是从网上搜索来的，出处很杂，零零碎碎存了好多tips，为了方便阅读和查找，使用LATEX编译成这个pdf文件。
曾经尝试用Word、Wikipad等工具整理，但都不如意。最近1才刚刚知道了LATEX，一边学习LaTex，一边试着用它整理这些笔记，所以有了这些文字。

由于正在学习LATEX，很多功能还不会用，只能先用基本格式排版，以后再慢慢完善格式。

1.2 为什么选Hyper-V与Linux？

常见的虚拟化产品大致可分为两类，一类是面向服务器的，另一类是面向工作站（桌面）的。

面向服务器的虚拟化产品主要就是VMware的ESXi（vSphere）和Windows Server的Hyper-V。面向桌面的虚拟化产品最常见的就是VMware Workstation了。

相对来说，Hyper-V上安装Windows比较容易，ESXi上安装Linux也比较容易，因为都是自家或同一家族的东西，兼容性还是不错的。但是说到在Hyper-V上安装Linux就有些不太顺畅了，所以才需要把笔记总结下来。

1.3 目标是什么？
在远程服务器上持续运行某个任务（不是httpd之类的服务，而是编译软件之类的任务），并且要求即使断开SSH客户端（如PuTTY）与服务器的连接，这些任务也会继续运行2直到完成。

以下是需要进行的工作清单：
1. 安装Linux；
2. 创建一个非root用户3；
3. 设置静态IP地址；
4. 安装ssh服务以便支持远程登录；
5. 使用PuTTY远程登录到Linux；
6. 安装screen；
7. 安装Hyper-V的Linux Integration Services；
8. 开启Hyper-V的Dynamic Memory（动态内存）功能；
9. 准备OpenWrt的编译环境；
10. 编译OpenWrt；
11. 验证编译结果，任务完成。

由于使用了screen，所以在编译时可以断开与远程主机的连接，过一段时间再使用screen重新连接到那个编译进程，查看进度和结果。

也就是说这个列表模拟了将一个需要持续运行一段时间的任务（编译OpenWrt）放到服务器后台运行，一直到任务结束。并且可以在编译完成时查看结果，也可以在编译过程中随时查看进度。而且在编译过程中，可以断开PuTTY和服务器的连接而不中断任务。

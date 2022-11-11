# Linux基础

Sylvie233的Linux学习~~~

> Author: Sylvie233
>
> Date: 2022/11/10
>
> Update: 2022/11/11
>
> Point: 

[TOC]

## Linux基础

GNU

gnu协议



POSIX标准

定义UNIX操作系统API接口规范



shell命令接收器

/bin/bash或/bin/sh

bash是linux的默认shell工具



### 常用快捷键



### 目录结构

文件/目录信息

```
drw-rw-r-- 硬链接次数 用户名 用户组 文件大小 日期 文件名
	d:
	rw-: 自己权限
	rw-: 组权限
	r--: 其它权限
	
```



inode存储文件信息



系统文件

```
/dev/null: 无底洞，可以向其输出任何内容
/dev/zero: 输入设备
```













































## Linux常用命令

### alias

定义别名

```
alias:
	
	
常用别名:
	ll: 
	
```





### apt-get

源服务器列表： `/etc/apt/sources.list`

```
apt-get:
	update: 更新源
	search: 搜索
	install: 安装
	remove: 删除
	--reinstall: 重新安装
	
apt-cache:
	search: 搜索
	show: 显示
	
```



### bg

任务切换到后台

```
bg:
	
```





### cat



```

```



### cd



```
cd
	-: 返回
	~: 用户家目录
	.: 当前目录
	..: 上级目录
	
```



### chgrp



```
chgrp:
	
```





### chmod



```
chmod:
	u/g/o/a: who
	+/-/: 增加、减少
	777: 数字方法修改
```



### chown

root权限

```
chown:
	_user:_group: 用户:用户组修改
```



### clear

清屏



### cp



```
cp:
	-r: 递归
```



### date

时间



### dpkg

deb包安装：.deb

```
dpkg:
	-i: 安装
	-r: 删除
	-info: 信息
```



### dd

拷贝

```
dd:
	if: 输入文件
	of: 输出文件
	
```





### df



```

```





### du



```
du:
	
```





### echo



```
echo:
	
	
常用变量:
	
```



### env

查看当前环境的环境变量

配置环境变量：`/etc/profile`

```
env:
	
	
常用环境变量:
	PATH: path路径
	SHELL: 使用的shell
	PWD: 当前目录
	HOME: 用户家目录
	
```



### exit

退出



### fdisk



```
fdisk:
	-l: 磁盘信息列表
```



### fg

唤醒任务：切换到前台

```
fg:
	
```



### file

查看文件信息

```
file:
	
```





### find

根据文件名查找

```
find:
	./: 目录
	-name: 文件名
	
```



### finger



```
finger:
	
```



### free

查看空闲内存

```
free:
	-m: 
```



### ftp

安装：`apt-get install vsftpd`

配置文件：`/etc/vsftpd.conf`

```
anonymous_enable=YES #
anon_root=/home/xxx #
no_anon_password=YES
anon_upload_enable=YES
anon_umask=022
anon_mkdir_write_enable=YES
local_enable=YES
local_umask=022
```



ftp使用

```
ftp _ip
	put: 上传
	get: 下载
	quit: 退出
	
```





```
ftp:
	
	
vsftpd:
	restart: 重启服务
    
upstart-job:
	
```



lftp客户端





### grep



```
grep:
	"xxx": 字符串内容
	./: 目录
	-R: 递归
```



### groupadd

添加用户组

```
groupadd:
	
```





### head



```
head:
	-n: 前n行
```





### history



```

```



### ifconfig

查看网卡信息

```
ifconfig:
	eth0: 网卡名
	up/down: 开启、关闭
```





### jobs



```
jobs:
	
```



### kill

进程发送信号

```
kill:
	-l: 信号列表
	_pid: 指定进程pid
	
	
信号列表:
	2: sigint
	9: sigkill
	11: sigsegv（段错误）
	19: sigstop（暂停）
	
```





### less



```
less:
	
```



### ln



```
ln:
	-s: 软链接
	
```





### ls



```
ls
	-a: 所有文件（隐藏文件）
	-l: 详细信息
	-R: 递归显示目录
```



### man

查看帮助手册

```
man:
	
	
	
分章节:
	
```





### mkdir



```
mkdir:
	-p: 递归创建
	
```



### more



```
more:
	
```



### mount

默认挂载到/media/目录下

```
mount:
	
```





### mv



```
mv:
	
```



### netstat



```
netstat:
	-a: 所有
	-t: tcp协议
	-n: 以ip代替名称相似
	
```



### nfs

网络目录映射挂载（目录共享）



安装：`apt-get install nfs-kernel-server`

配置：`/etc/exports`

```
nfs:
	
	
nfs-kernel-server:
	restart: 重启
```





### nslookup



```
nslookup:
	
```





### od



```
od:
	
```



### passwd

查看、修改用户密码

```

```



### ping



```
ping:
	
```



### poweroff

关机





### ps



```
ps:
	
	
常用:
	ps aux:
```





### pwd



```

```



### rar



```
rar:
	a: 打包
	
unrar:
	x: 解压
```



### reboot

重启



### rm



```
rm:
	-r: 递归删除
	-f: 强制
	-i: 询问
	
```



### rmdir



```
rmdir:
	
```



### shutdown

关机

```
shutdown:
	
```





### source

执行脚本

```
source:
	
. 同理
```



### ssh

远程登录



安装：`apt-get install openssh-server`

```
ssh:
	
```



ssh使用

```
ssh 用户名@_ip
```





### su

切换用户



### sudo



```

```



### tail



```
tail:
	-n: 末尾n行
```



### tar



```
tar:
	c: 创建
	r: 
	x: 解压缩
	z: gzip算法
	j: bzip2算法
	v: 详细信息
	f: 强制
	-C: 指定生成目录

常用:
	tar cvf xxx.tar xx : 创建压缩包
	tar xvf xxx.tar : 解压
```





### telnet

铭文传输数据

```
telnet:
	
```





### touch



```
touch:
	
```



### tree



```

```



### umask



```
umask

```





### umount



```
umount:
	
```



### uname



```
uname:
	-a: 内核版本
```





### useradd



```
useradd:
	-s: 指定使用shell
	-g: 用户组
	-d: 家目录
	-m: 用户名
	
```



### userdel



```
userdel:
	
```





### wc



```
wc:
	-c: 
	-l: 行数
```





### which



```
which
	
```



### who

查看登录用户

```
who:
	
```





### whoami



```

```







## Vim

### 基础

#### vim命令

```
vim: 
	-On: 分n左右屏打开
	--v: 查看vim版本
```



#### Vim IDE

vim配置文件：`vimrc`

```

```

注释：双引号`"`





### 常用快捷键

#### a

插入光标后



#### A

行尾插入



#### b

向前移动一个字



#### dd

删除光标所在行

删除指定行数：`ndd`

删除本行光标前内容：`d0`

删除光标所在字：`dw`



#### D

删除光标后本行所在



#### gg

移动到文件开头



#### G

移动到指定行：`nG`

默认移动到文件末尾



#### h

左移



#### i

插入到光标前



#### I

行首插入



#### j

下移



#### k

上移



#### K

查看man帮助手册

指定man手册的章节：`nK`



#### l

右移



#### L

移动到屏幕最后一行行首



#### M

移动到中间行



#### n

查找的下一个



#### o

下插入一行



#### O

上插入一行



#### p

在光标所在位置的下一行粘贴



#### r

替换当前字符



#### R

替换光标后字符



#### u

撤销



#### U

一次性撤销所有操作



#### v

可视模式，以字符为单位



#### V

可视模式，以行为单位



#### w

向后移动一个字



#### x

删除光标后一个字符



#### X

删除光标前一个字符



#### yy

复制当前行

复制n行：`nyy`



#### {

按段移动，上移



#### }

按段移动，下移



#### >>

文本行右移



#### <<

文本行左移



#### .

重复上一次命令



#### ctrl + r

反撤销



#### esc

进入命令模式



#### ：

进入末行模式

```
w: 写入
q: 退出
!: 强制

sp: 上下分屏
vsp: 左右分屏
	ctrl+w+w: 窗口切换
	
/: 查找

set: 设置
	nu: 设置行号
	nonu: 取消行号
	syntax: 语法高亮（on|off）
```







## Shell编程


# Makefile基础

Sylvie233的Makefile学习~~~

> Author: Sylvie233
>
> Date: 2022/11/14
>

[TOC]

## Makefile

```
Makefile:
	clean:
		.PHONY: clean :（伪目标声明，防止命令与文件重名）
		-: 出错继续执行
		@: 不显示命令本身
	distclean: 彻底清除（中间文件、配置文件）
	install: 安装（源码）
		
```



注释：#



构建依赖树

自上向下构建依赖，自下向上编译执行

比较文件修改时间

默认以第一个目录（可以显式指定）



变量

```
xxx = yyy
$(xxx)

常用变量:
	CPPFLAGS: 预处理标志
		-I: 指定include目录
	CFLAGS: 编译标志
		-g: 调试信息包含
		-Wall: 警告信息包含
		-On: 编译优化
	LDFLAGS: 链接标志
		-L: 指定lib目录
		-l: 指定库名
	CC: 使用的编译器
	

内置变量/通配符:
	%: 任意字符
	$@: 目标
	$^: 所有依赖
	$<: 依赖中的第一个
	
```



函数

```
内置函数:
    patsubst: 文件名替换
	wildcard: 查找符合条件的文件名
	
	
	
```













## Make

```
make:
	cmd: 指定目标命令
		clean: 清理
	-C: 指定makefile目录	
```


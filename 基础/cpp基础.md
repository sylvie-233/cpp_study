# C++基础

Sylvie233的C++学习~~~

> Author: Sylvie233
>
> Date: 2022/10/22



>Update: Sylvie233
>
>Point: 阿西拜C++基础教程P66



[TOC]

## C++介绍





## C++基础语法





## C++基础库

### C标准库

### \<cerrno>

#### errno

异常编号：`/usr/include/asm-generic/`

全局变量

```
errno: 
	EAGAIN: read重试（非阻塞）
```

常与perror联合使用



### \<cmath>





### \<cstdio>

#### FILE

#### rename

```
int rename(const char *oldpath, const char *newpath);
```





#### fclose

```

```





#### fopen

```

```



#### fputc

```

```





#### fseek

```
int fseek (FILE * stream, long int offset, int origin)
```



#### perror

```
void perror (const char * str)
```



#### printf

```

```



#### scanf

```

```



#### sprintf

```
int sprintf(char * str, const char * format, ...)
```





###  \<cstdlib>

#### exit

```
void exit (int status)
```



#### getenv

```
char* getenv(const char* name);
```







### \<cstring>

#### strerror

```
char * strerror (int errnum)
```



#### strlen

```
size_t strlen(const char * str)
```





### \<ctime>



###



### 容器

### 



### I/O



###

### 线程

### 

### 其它

### \<algorithm>









## gcc

### 基础

### 常用参数

```
gcc:
	-v: 版本
	--version: 版本
	-g: 包含调试信息
	-On: 编译优化
	-Wall: 提示更多警告信息
	-I: 指定include目录
	-D: 编译时定义宏
	-E: 生成预处理文件（生成.i文件）
	-c: 编译
	-fPIC: 生成与位置无关的.o文件
	-o: 指定输出名
	-M: 生成头文件、源文件依赖关系
	
	-shared: 动态库生成
	-soname: 指定动态库的soname（可执行文件中记录的动态库的版本信息）
```





## g++





## gdb

### 基础

GNU调试工具

命令分类：

```
help:
	aliases:
	breakpoints: 断点
	data:
	files:
	internals:
	obscure:
	running:
	stack:
	status:
	support:
	tracepoints:
	user-defined:
	
```



core文件

异常调试信息文件，可结合gdb使用



### 常用参数

```
gdb:
	list: 符号表（代码）
		n: 行号
		func_name: 指定函数名
	print: 打印
		var: 指定变量值|表达式
	info: 展示信息
		breakpoints: 断点列表
	backtrace: 栈帧信息
	set: 修改数据
		var: 变量
	delete: 删除
		breakpoints: 删除断点（指定编号）
	x: 查看内存
	help: 帮助
-----------------
	quit: 退出
	run: 运行（可传参）
	start: 启动（停在第一行），也可传参
	continue: 继续
	next: 单步执行、步过
	step: 步入
	finish: 结束当前函数
	frame: 切换栈帧
-----------------
	break: 断点
		n: 指定行号
	display: 设置观察变量（每次运行都会显示）
	undisplay: 删除观察变量
	watch: 监听变量（修改时显示）
```







## C++知识点补充

### binutils

一组用于编译、连接、汇编和其它调试目的的程序

```
gcc: 编译器
glibc: 实现Linux系统函数
ar: 生成静态库
as: 汇编器
ld: 链接器
nm: 查看符号表
objdump: 生成反汇编文件
ranlib: 为静态库文件创建索引
readelf: 解析ELF文件头



```


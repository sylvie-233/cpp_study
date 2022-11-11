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

### \<cmath>





### \<cstdio>

#### FILE



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

```



#### printf

```

```



#### scanf

```

```



### sprintf

```
int sprintf(char * str, const char * format, ...)
```





###  \<cstdlib>

#### exit

```
void exit (int status)
```





### \<cstring>

#### strlen

```
size_t strlen(const char * str)
```





### \<ctime>



### 

### 容器

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

### 常用参数

```
gdb:
	quit: 退出
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


# C++基础

Sylvie233的C++学习~~~

> Author: Sylvie233
>
> Date: 2022/10/22



>Update: Sylvie233
>
>Point: C++游戏服务器编程P31



[TOC]

## C++介绍

Visual Studio集成开发环境



C98、C03、C11、C14、C17、C20



文件后缀：`.cpp`、`.hpp`







## C++基础语法

### 基础语法

#### 关键字

```
关键字:
	alignas: 指定结构体字节对齐数，2的倍数（c++11）
	alignof: 查询字节对齐数（c++11）
	and: 逻辑与
	and_eq: &=
	asm: 汇编代码
	auto: 自动类型推断
	bitand: &
	bitor: |
	bool:
	break:
	case:
	catch:
	char:
	char16_t: （c++11）
	char32_6: （c++11）
	class:
	compl: ~
	concept: 概念
	const:
	constexpr: 编译期计算出常量值来，可用在函数上（c++11）
	const_cast<>(): const转换（去除）
	continue:
	decltype: 求表达式的类型，有括号为引用，在后置返回类型中与auto配合使用（c++11）
	default: 
	delete:
	do:
	double:
	dynamic_cast<>(): 父类指针转换为子类指针
	else:
	enum: 枚举、枚举类 enum class（默认int大小），
	explicit: 显示构造
	export:
	extern:
	float:
	for:
	friend: 友元单向
	goto:
	if:
	inline: 内联
	int:
	long:
	mutable:
	namespace:
	new:
	noexcept: 函数不会抛出异常，编译优化（c++11）
	not: !=
	not_eq: !=
	nullptr: 空指针（c++11）
	operator:
	or: |
	or_eq: |=
	private:
	protected:
	public:
	register: 变量放寄存器中
	reinterpret_cast<>(): 重解释转换，基于内存中的二进制数据表示（可用于无关类型转换），类似截断
	requires:
	return:
	short:
	signed:
	sizeof:
	static:
	static_assert: 编译器assert（c++11）
	static_cast<>(): 静态强转（相关类型转换）
	struct:
	switch:
	template:
	this:
	thread_local: （c++11）
	throw:
	true:
	try:
	typedef:
	typeid:
	typename:
	unino:
	unsigned:
	using: 可用来定义类型别名
	virtual:
	void:
	volatile: 不持久
	wchar_t:
	while:
	xor: ^
	xor_eq: ^=
```





#### 变量

```
const
```



#### 注释

```
//

/**/
```



#### 字面量

```

```





#### 预处理指令

```
#include

#define

#ifdef、#ifndef、#endif

#pragma: 编译器相关
	once: 引入一次
```



#### 表达式

```

```



#### 字符串

```

```



#### 数组

```

```



#### 函数

```

```





#### 命名空间

```
namespace xxx {
	
}

xxx::xxx

using namespace xxx;
```







### 控制语句























### 面向对象









### 指针









### 异常处理





### I/O



















### 多线程









## C++标准库

### Concepts library(概念)







### Coroutines library(协程)











### Utilities library(工具集)

#### \<cstddef>

##### byte



##### nullptr_t



##### NULL



##### size_t



##### 



##### 



####  \<cstdlib>

##### atoi

```
int atoi( const char *str );
```



##### exit

```
void exit (int status)
```



##### getenv

```
char* getenv(const char* name);
```



#### \<ctime>





#### \<functional>

##### cref

```
template< class T >
std::reference_wrapper<const T> cref( const T& t ) noexcept;
```



##### bind

```
template <class Fn, class... Args>  /* unspecified */ bind (Fn&& fn, Args&&... args);
template <class Ret, class Fn, class... Args>  /* unspecified */ bind (Fn&& fn, Args&&... args);
```





##### function

函数指针

```
template <class T> function;
```



##### placeholders

```
placeholders:
	_1:
	_2:
	_n:
```



##### ref

```
template< class T >
std::reference_wrapper<T> ref( T& t ) noexcept;
```





#### \<typeinfo>

```
namespace std {
  class type_info;
  class bad_cast;
  class bad_typeid;
}
```



##### typeid



##### type_info

```
namespace std {
  class type_info {
  public:
    virtual ~type_info();
    constexpr bool operator==(const type_info& rhs) const noexcept;
    bool before(const type_info& rhs) const noexcept;
    size_t hash_code() const noexcept;
    const char* name() const noexcept;
 
    type_info(const type_info&) = delete;                   // cannot be copied
    type_info& operator=(const type_info&) = delete;        // cannot be copied
  };
}
```









#### \<utility>

##### pair

```
template <class T1, class T2> struct pair;
	first:
	second:
```



##### forward

```
template <class T> T&& forward (typename remove_reference<T>::type& arg) noexcept;
template <class T> T&& forward (typename remove_reference<T>::type&& arg) noexcept;
```





##### make_pair

```
template <class T1, class T2>  pair<T1,T2> make_pair (T1 x, T2 y);
```



##### move

```
template <class T>typename remove_reference<T>::type&& move (T&& arg) noexcept;
```









### Dynamic memory management(动态内存管理)

#### \<memory>

##### make_shared

```
template <class T, class... Args>
shared_ptr<T> make_shared(Args&&... args);
```





##### make_unique

```
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);
// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);
// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```



##### shared_ptr

```
shared_ptr:
	use_count: 引用计数
```





##### unique_ptr

```
unique_ptr:
	get: 获取地址
	reset: 重置
	*: 解引用
```



##### weak_ptr

循环依赖问题



```
weak_ptr:
	use_count: 
	lock: 转为shared_ptr
```







### Numeric limits(数值限制)









### Error handling(异常处理)

```
namespace std {
    class logic_error;
    class domain_error;
    class invalid_argument;
    class length_error;
    class out_of_range;
    class runtime_error;
    class range_error;
    class overflow_error;
    class underflow_error;
}
```

#### \<cerrno>

##### errno

异常编号：`/usr/include/asm-generic/`

全局变量

```
errno: 
	EAGAIN: read重试（非阻塞）
```

常与perror联合使用



#### \<exception>

##### exception

```
namespace std {
  class exception {
  public:
    exception() noexcept;
    exception(const exception&) noexcept;
    exception& operator=(const exception&) noexcept;
    virtual ~exception();
    virtual const char* what() const noexcept;
  };
}
```



##### terminate

```
[[noreturn]] void terminate() noexcept;
```





#### \<stdexception>

```

```



##### runtime_error

```
namespace std {
  class runtime_error : public exception {
  public:
    explicit runtime_error(const string& what_arg);
    explicit runtime_error(const char* what_arg);
  };
}
```







### Strings library(字符串)

#### \<cstring>

##### strerror

```
char * strerror (int errnum)
```



##### strlen

```
std::size_t strlen( const char* str );
```



#### \<string>

##### string

```

```









### Containers library(容器)

#### \<vector>





















### Iterators library(迭代器)















### Ranges library(范围)























### Algorithms library(算法)

#### \<algorithm>

##### reverse

```
template< class BidirIt >
void reverse( BidirIt first, BidirIt last );
```



##### sort

```

```





##### swap

```
template <class T> void swap (T& a, T& b);
```















### Numerics library(数值运算)

#### \<cmath>















### Localization library(本地化)





















### Input/output library(输入、输出)

#### \<cstdio>

##### FILE







##### rename

```
int rename(const char *oldpath, const char *newpath);
```





##### fclose

```

```





##### fopen

```

```



##### fputc

```

```





##### fseek

```
int fseek (FILE * stream, long int offset, int origin)
```



##### perror

```
void perror (const char * str)
```



##### printf

```

```



##### scanf

```

```



##### sprintf

```
int sprintf(char * str, const char * format, ...)
```





#### \<fstream>



#### \<istream>

##### istream

```

```





#### \<iostream>

##### cerr

```

```



##### cin

```

```



##### clog

```

```



##### cout

```

```



#### \<ostream>

##### endl

```

```





##### ostream

```

```











### Filesystem library(文件系统)

















### Regular Expressions library(正则表达式)























### Atomic Operations library(原子操作)























### Thread support library(线程)

#### \<thread>



















## gcc

### 基础

### 常用参数

```
gcc:
	-v: 版本
	--version: 版本
	-g: 包含调试信息
	-On: 编译优化
	-std: 指定c++版本
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
binutils:
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



### clang

llvm苹果开源编译项目的子项目

```
clang:
	--version:
	
clang++:
	
```


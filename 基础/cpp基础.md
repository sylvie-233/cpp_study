# C++基础

Sylvie233的C++学习~~~

> Author: Sylvie233
>
> Date: 2022/10/22

>Update: Sylvie233
>
>Point: 现代C++教程P31 | C++20 STL P11



[TOC]

## 基础介绍

Visual Studio集成开发环境



C98、C03、C11、C14、C17、C20



文件后缀：`.cpp`、`.hpp`

### vcpkg

```
vcpkg:
	
```







## 核心内容

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

![image-20230608201104966](cpp基础.assets/image-20230608201104966.png)



右值的出现可更好的避免内存拷贝(移动构造)、优化拷贝开销









##### using类型别名





##### auto类型推断



##### constexpr



##### decltype





#### 注释

```
//

/**/
```



#### 字面量

```
using namespace std::literals;

auto str = "233"s; // string
```





##### 用户自定义字面量

```
std::string operator""_r(const char* std, size_t size) { // _r是自定义的
	return { str };
}

int main() {
	std::cout << "233"_r << '\n';
}
```









#### 预处理指令

```
#include

#define

#ifdef、#ifndef、#endif

#pragma: 编译器相关
	once: 引入一次
	
#error: 错误输出
```



##### 宏



###### 变长实参







#### 字符串

##### string



##### basic_string





##### basec_string_view









#### 数组

```

```



#### 函数

##### 默认参数



##### lambda

```
auto func = []<typename T> (T arg) {}
```





#### 结构体

##### 聚合初始化











#### 命名空间

```
namespace xxx {
	
}

xxx::xxx

using namespace xxx;
```



#### 模块

```
module;

export module xxx;

export void func();

export {
	xxx
}

export namespace xxx {
	
}

export import xxx;

---
import <iostream>;

import xxx;
```







#### 控制语句



##### 三路比较

```
a <=> b
```





##### 结构化绑定

```
auto [x, y] = a;
```

















### 面向对象

#### 成员函数

##### default



##### delete

弃置函数







##### 有引用限定的成员函数



#### 构造函数

##### explicit







##### initializer_list初始化列表构造











### 模板

#### 类模板







#### 模板推导指引

##### enable_if

##### enable_if_t

##### is_same

##### is_same_v





#### 字符串字面量运算模板



#### 模板模板形参

#### 形参包

可变参数模板



##### 类型约束

```
:
	Integral:
	
```



##### 折叠表达式





#### 变量模板





#### 概念、约束

requires 类型约束

concept 类型概念

概念是一组命名到约束，可在模板中直接使用概念	





### 指针

#### unique_ptr

```

```



#### shared_ptr

```

```



#### weak_ptr

弱引用，不增加计数、解决循环引用问题（配合shared_ptr使用）

```

```





#### 成员函数指针





使用样例

```
struct X {
	void f() {std::cout << "6";}
};

void f2(void (X::*p) (), X& x) {
	(x.*p)();
}

int main() {
	X x;
	f2(&X::f, x); // 6
}
```



#### 数据成员指针





使用样例

```
struct X {
	int x = 1;
};

int main() {
	int X::* n = &X::x;
	X x;
	x.*n; // 1
}
```













#### 引用

纯右值、将亡值



##### 右值引用



##### 移动语义

`std::move()`与移动构造函数



##### 完美转发

在函数模板中，可以将参数“完美”的转发给其它函数。即不仅能准确的转发参数的值，还能保证被转发参数的左、右值属性不变

`std::forward()`



智能指针的删除器





### 异常处理

#### noexcept

```
void func() noexcept {}


noexcept(expr); // 返回bool类型的纯右值
```





### STL容器





### 元编程



### I/O



















### 多线程





### 协程











## API

```
<algorithm>
    accumulate():
	equal_range():

<any>
	any:
<array>
	array:

<atomic>
<barrier>
<bit>
<bitset>
	bitset:
		
<cassert>
	static_assert():

<cctype>
<cerrno>
<cfenv>
<charconv>
	from_chars():
	to_chars():
	
<chrono>:
	milliseconds:
	seconds:
	steady_clock:
		time_point:
		now():
	
<cmath>
<compare>
	partial_ordering:
	strong_ordering:
		greater:
		less:
		qeual:
		

<complex>
<concepts>
	concept:
	requires:

<condition_variable>
	condition_variable:
		---
		notify_one():
		wait():
		wait_for():	
		wait_until():
		
<coroutine>
<cstdarg>
<cstddef>
<cstdio>
<cstdlib>
<cstring>
<ctime>
<cuchar>
<deque>
	deuqe:
		front():
		push_back():

<exception>
<execution>
<expected>
	expected:
<fstream>
<functional>
	bind():
	cref():
	function<T>():
	invoke():
	ref(): 引用标记
<future>
	future:
		get():
		shared():
		wait_for():
		wait_until():
	launch:
		async:
		deferred:
	packaged_task:
		get_future():
	promise:
		get_future():
		set_value():
    shared_future:
	async():
	
<filesystem>
	filesystem:
		copy_options:
			recursive:
		path:
			operator/():
			---
			extension():
			filename():
			is_absolute():
			is_relative():
			parent_path():
			relative_path():
			stem():
		directory_iterator:
			---
			path():
		recusive_direcctory_iterator:
			---
			path():
		absolute():
		copy():
		copy_file():
		current_path():
		exists():
		is_directory():
		is_regular_file():
		remove():
		remove_all():


<flat_map>
<flat_set>
<format>:
	formatter: 格式器特化
		format():
		parse():
	format():
	format_to():
	make_format_args():
	vformat():
	
<forward_list>
<initializer_list>
	initializer_list:

<iomanip>
<iostream>
	ostream:


<ios>
	basic_iostream:
	ios_base:
<iterator>
<latch>
<list>
<map>
<mdspan>
<memory>
	enable_shared_from_this:
	make_shared():
	shared_from_this():
<memory_resource>


<mutex>
	adopt_lock:
	defer_lock:
	lock_guard: 锁守卫
	mutex:
		---
		lock():
		try_lock_for():
		try_lock_until():
		unlock():
	once_flag: 一次性标志
	unique_lock:
		lock():
		unlock():
	call_once(): 借助flag实现一次调用
	lock():
	
	
<new>
<numbers>
<optinal>
	optional:
<print>
	print():
		
<queue>
<random>
<ranges>: 流式操作
	ranges:
		range:
		copy():
		sort():	
    views: 可借助管道符使用
    	drop():
    	filter():
    	iota():
        reverse():
        take():
        transform():
    take_view():

<ratio>
<regex>
	regex:
		icase:
	regex_error:
		code():
	smatch:
		matched:
		str():
	sregex_iterator:
		prefix():
		str():
		suffix():
	regex_replace():
	regex_search():


<scoped_allocator>
<semaphore>
<set>
<shared_mutex>
<source_location>
<span>: 包装器，可在连续对象上创建视图
	span:
		back():
		begin():
		data():
		empty():
		end():
		front():
		rbegin():
		rend():
		size():
		size_bytes():
	
<spanstream>
<sstream>
<stack>
<stacktrace>
<stdexcept>
<stdfloat>
<stop_token>
<string>
	basic_string:
	literals:
		""s:
		chrono_literals:
			ms:
			s:
			
	string:
		c_str():
	to_string():
<string_view>
	string_view:

<syncstream>
<system_error>
<thread>
	this_thread:
		get_id():
		sleep_for():
		sleep_until():
	thread:
		hardware_concurrency():
		---
		detach(): 分离线程
		get_id():
		join():
		joinable():
		
<tuple>
	tuple:
		
	tuple_element:
		type:
	tuple_size:
		valu:
	get():
	make_tuple():
	
	
<type_traits>
	floating_point:
	integral:
	is_integral_v:
	is_pointer_v:
	is_same_v:
	is_signed:
	is_signed_v:
	make_unsigned_t:

<typeindex>
<typeinfo>
<unordered_map>
<unordered_set>
<utility>
	cmp_less():
	move():
	
	
<variant>
	variant:
	
<vector>
	vector:
		const_iterator:
		size_type:
		cbegin():
		cend():
		
<version>: 宏定义
	__cpp_lib_format:
	has_include():
	

```



### 概念库







### 协程库











### 工具库

#### \<chrono>

##### chrono

```
chrono:
	duration_cast:
	system_clock:
		time_point:
		now():
	milliseconds():
	minutes():
	seconds():
	
```



#### \<csignal>

##### raise

```

```



##### signal

```

```





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



##### rand

```
int rand();
```



##### srand

```
void srand( unsigned seed );
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









### 动态内存管理

#### \<memory>

##### enable_shared_from_this

```
:
	shared_from_this():
```



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
	*: 解引用
	get(): 获取地址
	release():
	reset(): 重置
	
```



##### weak_ptr

循环依赖问题



```
weak_ptr:
	use_count: 
	lock(): 转为shared_ptr
	expired():
```







### Numeric limits(数值限制)









### Error handling(异常处理)

#### \<cassert>

##### assert

```
ifdef NDEBUG
  define assert(condition) ((void)0)
else
  define assert(condition) /*implementation defined*/
endif
```





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



##### to_string







### Containers library(容器)

#### \<array>

```
array<typename T, size_t N>:
	[]:
	at():
	back():
	empty():
	fill():
	front():
	max_size():
	size():
	swap():
```



#### \<deque>

```
deque<typename T, typename Allocator = allocator<T>>:
	assign():
	at():
	back():
	begin():
	clear():
	emplace_back():
	emplace_front():
	empty():
	end():
	erase():
	front():
	max_size():
	pop_back():
	pop_front():
	push_back():
	push_front():
	shrink_to_fit():
	size():
```



#### \<forward_list>

```
forward_list<typename T, typename Allocator = allocator<T>>:
	assign():
	before_begin():
	begin():
	empty():
	end():
	erase_after():
	front():
	insert_after():
	pop_front():
	push_front():
	swap():
```



#### \<list>

```
list<typename T, typename Allocator = allocator<T>>:
	assign():
	back():
	begin():
	empty():
	end():
	front():
	merge():
	pop_back():
	pop_front():
	push_back():
	push_front():
	remove():
	reserve():
	resize():
	size():
	sort():
	splice():
	swap():
	unique():
```



#### \<map>

```
map<typename Key, typename T, typename Compare = less<Key>, typename Allocator = allocator<pair<const Key, T>>>:
	begin():
	count(): 
	end():
	find():
	lower_bound():
```



#### \<queue>

```

```



#### \<set>

```
set<typename T, typename Compare = less<T>, typename Allocator = allocator<T>>:
	begin():
	count():
	empty():
	end():
	find():
	lower_bound():
	key_comp():
	size():
	upper_bound():
	value_comp():

multiset<typename T, typename Compare = less<T>, typename Allocator = allocator<T>>:
```



#### \<stack>

```

```



#### \<unordered_map>

```
unordered_map<typename Key, typename T, typename Hash = hash<Key>, typename EqPred = equal_to<Key>, typename Allocator = allocator<pair<const Key, T>>>:
	
```



#### \<unordered_set>

```

```



#### \<vector>

```
vector<typename T, typename Allocator = allocator<T>>:
	[]:
	assign():
	at():
	back():
	begin():
	capacity():
	cbegin():
	cend():
	clear():
	crbegin():
	crend():
	emplace():
	emplace_back():
	empty():
	end():
	erase():
	front():
	insert():
	max_size():
	pop_back():
	push_back():
	rbegin():
	rend():
	reserve():
	resize():
	shrink_to_fit():
	size():
	swap():
```



















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

##### fstream

##### ios_base

```
ios_base:
	
```





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

#### \<atomic>

##### atomic

```
atomic<T>:
	fetch_add():
	fetch_sub():
```



##### atomic_int























### Thread support library(线程)

#### \<condition_variable>

##### condition_variable

```
condition_variable:
	notify_all():
	notify_one():
	wait():
```





#### \<future>

##### async



##### future

```
std::future<T>:
	get():
```



##### launch

```
std::launch:
	async:
```





#### \<mutex>

##### adopt_lock

##### lock

##### lock_guard

```
lock_guard<T>:
	
```



##### mutex

```
mutex<T>:
	lock():
	unlock():
```



##### unique_lock

```
unique_lock<T>:
	
```







#### \<thread>

##### this_thread

```
this_thread:
	get_id():
	sleep_for():
	yield():
```





##### thread

```
thread:
	detach():
	get_id():
	hardware_concurrency()
	join():
	joinable():
```



















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

```
g++:
	
```







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
	-p: 进程号
	-x: 携带断点信息文件（bp文件）
	--version: 版本
	core文件: 记录错误信息
-----------------
    bt/backtrace: 栈帧信息
    b/break: 断点
        _n: 指定行号
        函数名: 指定函数名
        文件名:行号: 指定文件的行号
        *_addr: 指定地址
    c/continue: 继续
	d/delete: 删除
		_n: 删除指定序号的断点
		display: 删除指定编号的display变量
		breakpoints: 删除断点（指定编号）
	disable:
		breakpoinst: 禁用断点
		display: 禁用指定编号的display变量
	disas: 显示当前的汇编代码，或指函数的汇编代码
		/m: 源码显示
		/r: 16进制显示
	display: 设置观察变量（每次运行都会显示）
		/f: 
		/x: 用十六进制看寄存器的中
		/i $pc: 用汇编代码看下一步要执行的指令
	enable:
		breakpoints: 启用断点
		display: 启用指定编号的display变量
	file: 加载指定可执行程序
	finish: 结束当前函数，回到函数调用点
	frame: 切换栈帧
	help: 帮助
	i/info: 展示信息
		r: 显示指定的寄存器的值
		b/breakpoints: 断点列表
		display: 查看display变量
		line: 指定行
		watchpoints: 观察点列表
	layout: 切换视图
		asm: 汇编视图
	l/list: 符号表（代码）
		n: 行号
		func_name: 指定函数名
	n/next: 单步执行、步过
		ni: 单条指令
	p/print: 打印
		var: 指定变量值|表达式
	q/quit: 退出
	r/run: 运行（可传参）
	save
		breakpoint:保存断点
	set: 修改数据
		var: 变量（$pc, $eflags,）
		logging: 日志开启（on/off），gdb.txt日志输出文件
	start: 启动（停在第一行），也可传参
    shell: 执行shell命令
	s/step: 步入
		si: 单条指令步入
	undisplay: 删除观察变量
	watch: 监听变量（修改时显示）
	x: 查看内存
		/n: 显示内存单元的个数
		/i: 显示汇编指令
		/f: 输出格式（s字符串、x十六进制、d十进制、t二进制）
		/u: 类型字节数（每个内存单元占字节数）（默认4字节，b1、h2、w4、g8）
-----------------
	enter: 回车（重复上一条指令）
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



### objdump

```
objdump:
	-d: 复制内存指令dump
```


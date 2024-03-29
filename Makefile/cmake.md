# CMake

> Author: Sylvie233
>
> Date: 23/5/13
>
> Point: P15

[TOC]

## 基础介绍

### 编译生成

```
:
	/CMakeFiles:
	CMakeCache.txt:
	Makefile:
	cmake_install.cmake:
```





### 注释

```
# 行注释

#[[
	块注释
]]
```







### cmake

```
cmake:
	-D: 自定义变量（宏）
	--- 常用变量:
	CMAKE_INSTALL_PREFIX:
```



### CMakeLists.txt

```
cmake_minimum_required(VERSION 3.16)		# cmake版本
	# VERSION:
project(XXX CXX) 							# 项目名
	# 隐式定义变量
	#	<projectname>_BINARY_DIR
	#	<projectname>_SOURCE_DIR
	# project(<PROJECT-NAME>
    #    [VERSION <major>[.<minor>[.<patch>[.<tweak>]]]]
    #    [DESCRIPTION <project-description-string>]
    #    [HOMEPAGE_URL <url-string>]
    #    [LANGUAGES <language-name>...])

	
add_subdirectory(src bin)					# 添加子项目src（自动生成bin目录：编译输出目录）

aux_source_directory(dir var)				# 搜索源文件赋给变量
file(GLOB/GLOB_RECURSE 变量名 搜索匹配)		# 文件搜索

find_package()								#

install(FILES xxx xxx DESTINATION /xxx/xxx)	# 安装文件到指定目录 （生成内容可 make install 安装）
	# 默认安装到 CMAKE_INSTALL_PREFIX所指向的目录
	#	安装其它文件：
	#		PROGRAMS: 脚步文件
	#		DIRECTORY: 目录
	#		TARGETS: 库文件
	#			LIBRARY DESTINATION: 动态库
	#			ARCHIVE DESTINATION: 静态库
	#			RUNTIME DESTINATION: 二进制文件（头文件用FILES）
	
add_definitions(宏定义)
	
set(XXA XXB)								# 设置变量A的值
	# TRUE|FLASE
list(APPEND <list> [<element> ...])			# 字符串追加
	# 	APPEND: 追加
	#	PREPEND: 前加
	#	POP_BACK:
	#	POP_FRONT:
	#	REMOVE_ITEM: 移除
	#	REMOVE_AT:
	#	REMOVE_DUPLICATES:
	#	LENGTH: 长度
	#	GET: 获取指定索引数据
	#	FIND: 查找(-1)
	#	INSERT:	插入
	#	REVERSE:
	#	SORT:	list (SORT <list> [COMPARE <compare>] [CASE <case>] [ORDER <order>])
	
	
	
message(STATUS "xxx")						# 输出自定义信息
	#	message([STATUS|WARNING|AUTHOR_WARNING|FATAL_ERROR|SEND_ERROR] "message to display" ...)
	#	SEND_ERROR
	#	STATUS
	# 	FATAL_ERROR
	
include_directories(/xxx/xxx)				# 添加头文件目录
link_directories(/xxx/xxx)					# 添加库目录
link_libraries(xxx)							# 链接静态库
	
	
add_library(hello SHARED ${LIB_SRC})		# 生成库文件
	#	SHARED: 动态库文件 
	#	STATIC:	静态库文件
add_executable(hello ${SRC_LIST})			# 生成可执行文件
target_link_libraries(hello libxxx.so)		# 链接动态库，插入链接共享库（动态库|静态库）
	#	-static: 静态插入
	# target_link_libraries(
    # 	<target> 
    # 	<PRIVATE|PUBLIC|INTERFACE> <item>... 
    # 	[<PRIVATE|PUBLIC|INTERFACE> <item>...]...)



set_target_properties(hello PROPERTIES OUTPUT_NAME "233")						# 设置输出属性
	#	CLEAN_DIRECT_OUTPUT: 
	#	OUTPUT_NAME: 目标输出文件名
	#	SOVERSION:
	#	VERSION:
	
# ----------------------- 常用变量
CMAKE_BUILD_TYPE:
CMAKE_CXX_STANDARD: c++版本
CMAKE_INCLUDE_PATH:
CMAKE_LIBRARY_PATH:
```







## 核心内容

### 变量

```
set(Var Value)	# 定义变量
${Var}			# 使用变量	
```



子项目中可使用父项目中定义的变量





#### 预定义变量

```
宏:
	CMAKE_CURRENT_SOURCE_DIR: CMakeLists.txt当前目录
	CMAKE_CXX_STANDARD: c++版本
	EXECUTABLE_OUTPUT_PATH: 可执行程序输出路径
	LIBRARY_OUTPUT_PATH: 库文件输出路径
	PROJECT_SOURCE_DIR: CMakeLists.txt当前目录
```



### 流程控制





## API

### add_definitions



### add_executable

生成可执行文件





### add_library

生成库文件：STATIC、SHARED



### add_subdirectory

添加子项目



### aux_source_directory

搜索源文件







### cmake_minimum_required

指定最低cmake版本







### file

文件搜索



### include_directories

头文件目录制定



### link_directories

链接库文件所在目录



### link_libraries

链接库文件（根据link_directories目录查找）



### list

```
list(APPEND <list>) # 追加字符串

list(REMOVE_ITEM <list> <value...>) # 删除字符串

list(LENGTH <list> <output variable>) # 获取列表长度

list(GET <list> <index...>  <output>) # 索引

list<JOIN <list> <glue> <output>) # 拼接

list(FIND <list> <value> <output>) # 查找

list(INSERT)

list(PREPEND)

list(POP_BACK)

list(POP_FRONT)

list(REMOVE_AT <list> <index...>)

list(REVERSE)

list(SORT <list> [COMPARE <compare>] [CASE <case>] [ORDER <order>])
	COMPARE:
		STRING:
		FILE_BASENAME:
		MATURAL:
	CASE:
		SENSITIVE:
	ORDER:
		
		
```





### message



### project

指定项目名



### set

设置变量值



### target_link_libraries

指定目标链接库文件（动态库、静态库）






















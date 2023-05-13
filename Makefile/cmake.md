# CMake

> Author: Sylvie233
>
> Date: 23/5/13
>
> Point:

[TOC]

## 基础介绍



### cmake

```
cmake:
	-D: 自定义变量
	--- 常用变量:
	CMAKE_INSTALL_PREFIX:
```



### CMakeLists.txt

```
project(XXX CXX) 							# 项目名
	# 隐式定义变量
	#	<projectname>_BINARY_DIR
	#	<projectname>_SOURCE_DIR
	
add_subdirectory(src bin)					# 添加子项目src（自动生成bin目录：编译输出目录）

install(FILES xxx xxx DESTINATION /xxx/xxx)	# 安装文件到指定目录 （生成内容可 make install 安装）
	# 默认安装到 CMAKE_INSTALL_PREFIX所指向的目录
	#	安装其它文件：
	#		PROGRAMS: 脚步文件
	#		DIRECTORY: 目录
	#		TARGETS: 库文件
	#			LIBRARY DESTINATION: 动态库
	#			ARCHIVE DESTINATION: 静态库
	#			RUNTIME DESTINATION: 二进制文件（头文件用FILES）
	
set(XXA XXB)								# 设置变量A的值

message(STATUS "xxx")						# 输出自定义信息
	#	SEND_ERROR
	#	STATUS
	# 	FATAL_ERROR
	
include_directories(/xxx/xxx)				# 添加头文件目录
link_directories(/xxx/xxx)					# 添加共享库目录
	
	
add_library(hello SHARED ${LIB_SRC})		# 生成库文件
	#	SHARED: 动态库文件 
	#	STATIC:	静态库文件
add_executable(hello ${SRC_LIST})			# 生成可执行文件

target_link_libraries(hello libxxx.so)		# 插入链接共享库（动态库|静态库）

set_target_properties(hello PROPERTIES OUTPUT_NAME "233")						# 设置输出属性
	#	CLEAN_DIRECT_OUTPUT: 
	#	OUTPUT_NAME: 目标输出文件名
	#	SOVERSION:
	#	VERSION:
	
# ----------------------- 常用变量
CMAKE_BUILD_TYPE:
CMAKE_INCLUDE_PATH:
CMAKE_LIBRARY_PATH:
```







## 核心内容










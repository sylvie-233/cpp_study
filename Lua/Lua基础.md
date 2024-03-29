# Lua基础

> Author: Sylvie233
>
> Date: 23/1/1
>
> Point：Unity Lua P5

[TOC]

## 基础介绍

lua是纯c代码编写



lua字节码



安装目录：

```
dir:
	/bin:
	/doc:
	/etc:
	/include:
	/lib:
	/src:
	/test:
	Makefile:
	INSTALL:
	config:
	configure:
	build:
```









### lua

```
lua:
	
```



### luac

```
luac:
	-l: 列出字节码信息
	-o: 输出字节码
	-s: 去处调试信息
```





## lua核心

### 变量

动态语言

支持解构语法



local局部变量



数据类型：

```
数据类型：
	nil:
	boolean:
	number:
	string:
	function:
	userdata:
	thread:
```



字符串

```
""
''
[[ 多行字符串 ]]
```

字符串连接：`..`

字符串长度：`#str`



注释

```
-- 单行

--[[
	多行
]]
```





### 表达式

```
表达式：
	local、
	nil、true、false
	not、and、or、
	+、-、*、/、
	==、~=、
	..、
	--
	
```





### 控制语句

```
控制语句：
	if、then、else if、else、end
	for、=、do、end
	for、in、do、end
	while、do、end
	repeat、until
	break、return
```





### 函数

function定义

```
function 函数名(参数列表)
	return xxx
end
```



可变参数：`...`、`arg`表



闭包



只有一个参数，调用时括号可省



尾调用不消耗堆栈



### table元表

数据可用table实现

```
x = {1, 2, 3}

x[1]
```



```
x = {k=v,}

x.k
x:func() 等价于 x.func(x)
self

x["k"]
```



元表即table的特殊操作符表，可进行绑定



弱表



### userdata



### 协程

thread



### 包模块





### Lua与C

c引入lua

```
#include <lua.h>
#include <lauxlib.h>
#include <lualib.h>

lua_State变量：状态保存
```



通过堆栈通信

<img src="Lua基础.assets/image-20230105144658350.png" alt="image-20230105144658350" style="zoom:67%;" />





## 标准库模块

### basic

#### _G

全局环境表



#### _VERSION
#### assert

断言



#### collectgarbage

手动垃圾回收



#### dofile
#### error

抛出错误



#### getmetatable

获取table绑定的元表



#### ipairs

常与for、in连用



#### load
#### loadfile
#### next
#### pairs
#### pcall





#### print

控制台打印



#### rawequal
#### rawget

不会访问元表中的\_\_index函数



#### rawlen
#### rawset
#### require

引入package包



#### select
#### setmetatable

table绑定元表



#### tonumber

变量转换为数值



#### tostring

变量转换为字符串



#### type

查看变量类型、返回string



#### warn
#### xpcall



### coroutine

```
coroutine:
	create():
	resume():
	status():
	wrap():
	yield():
```



### debug

```
debug:
	getinfo():
```



### io

```
io:
	lines():
```



### math



### os



### package

```
package:
	cpath:
	loaded: 已加载的包（一个table）
	path:
	preload:
	
```



### string

```
string:
	byte(): 转ASCII码
	char(): ASCII转字符
	find(): 索引从1开始
	format(): 字符串格式化
	gsub(): 替换
	lower(): 转小写
	rep(): 重复
	reverse(): 翻转
	sub(): 截取
	upper(): 转大写
	
```



### table

```
table:
	getn():
	insert():
	remove():
	sort():
```





### utf8



### metamethods

#### \_\_add

加法运算符



#### \_\_band

#### \_\_bnot

#### \_\_bor

#### \_\_bxor

#### \_\_call

函数调用操作符



#### \_\_close

#### \_\_concat

连接运算



#### \_\_div

除法运算符



#### \_\_eq

相等运算符



#### \_\_gc

#### \_\_idiv

#### \_\_index

索引运算符



#### \_\_le

#### \_\_len

#### \_\_lt

小于运算符



#### \_\_metatable

#### \_\_mod

#### \_\_mode

弱表模式

`"k"`、`"v"`、`"kv"`



#### \_\_mul

#### \_\_name

#### \_\_newindex

索引添加元素



#### \_\_pairs

#### \_\_pow

#### \_\_shl

#### \_\_shr

#### \_\_sub

#### \_\_tostring

转换为字符串tostring函数、print函数



#### \_\_unm



### 环境变量

#### LUA_CPATH
#### LUA_CPATH_5_4
#### LUA_INIT
#### LUA_INIT_5_4
#### LUA_PATH
#### LUA_PATH_5_4



### C API
#### lua_Alloc
#### lua_CFunction
#### lua_Debug
#### lua_Hook
#### lua_Integer
#### lua_KContext
#### lua_KFunction
#### lua_Number
#### lua_Reader




#### lua_State

lua状态保存结构体



#### lua_Unsigned
#### lua_WarnFunction
#### lua_Writer
#### lua_absindex
#### lua_arith
#### lua_atpanic
#### lua_call
#### lua_callk
#### lua_checkstack
#### lua_close
#### lua_closeslot
#### lua_compare
#### lua_concat
#### lua_copy
#### lua_createtable
#### lua_dump
#### lua_error
#### lua_gc
#### lua_getallocf
#### lua_getextraspace
#### lua_getfield




#### lua_getglobal

获取全局函数，传入栈中





#### lua_gethook
#### lua_gethookcount
#### lua_gethookmask
#### lua_geti
#### lua_getinfo
#### lua_getiuservalue
#### lua_getlocal
#### lua_getmetatable
#### lua_getstack
#### lua_gettable
#### lua_gettop
#### lua_getupvalue
#### lua_insert
#### lua_isboolean
#### lua_iscfunction
#### lua_isfunction
#### lua_isinteger
#### lua_islightuserdata
#### lua_isnil
#### lua_isnone
#### lua_isnoneornil
#### lua_isnumber
#### lua_isstring
#### lua_istable
#### lua_isthread
#### lua_isuserdata
#### lua_isyieldable
#### lua_len
#### lua_load


#### lua_newstate

新建lua_State变量



#### lua_newtable
#### lua_newthread
#### lua_newuserdatauv
#### lua_next
#### lua_numbertointeger





#### lua_pcall
调用栈中函数



#### lua_pcallk





#### lua_pop

弹栈操作



#### lua_pushboolean
#### lua_pushcclosure
#### lua_pushcfunction
#### lua_pushfstring
#### lua_pushglobaltable
#### lua_pushinteger
#### lua_pushlightuserdata
#### lua_pushliteral
#### lua_pushlstring
#### lua_pushnil
#### lua_pushnumber
#### lua_pushstring
#### lua_pushthread
#### lua_pushvalue
#### lua_pushvfstring
#### lua_rawequal
#### lua_rawget
#### lua_rawgeti
#### lua_rawgetp
#### lua_rawlen
#### lua_rawset
#### lua_rawseti
#### lua_rawsetp
#### lua_register
#### lua_remove
#### lua_replace
#### lua_resetthread
#### lua_resume
#### lua_rotate
#### lua_setallocf
#### lua_setfield
#### lua_setglobal
#### lua_sethook
#### lua_seti
#### lua_setiuservalue
#### lua_setlocal
#### lua_setmetatable
#### lua_settable
#### lua_settop
#### lua_setupvalue
#### lua_setwarnf
#### lua_status
#### lua_stringtonumber
#### lua_toboolean
#### lua_tocfunction
#### lua_toclose
#### lua_tointeger





#### lua_tointegerx
#### lua_tolstring
#### lua_tonumber
数字转换



#### lua_tonumberx

#### lua_topointer
#### lua_tostring
#### lua_tothread
#### lua_touserdata
#### lua_type
#### lua_typename
#### lua_upvalueid
#### lua_upvalueindex
#### lua_upvaluejoin
#### lua_version
#### lua_warning
#### lua_xmove
#### lua_yield
#### lua_yieldk



### auxiliary library
#### luaL_Buffer
#### luaL_Reg
#### luaL_Stream
#### luaL_addchar
#### luaL_addgsub
#### luaL_addlstring
#### luaL_addsize
#### luaL_addstring
#### luaL_addvalue
#### luaL_argcheck
#### luaL_argerror
#### luaL_argexpected
#### luaL_buffaddr
#### luaL_buffinit
#### luaL_buffinitsize
#### luaL_bufflen
#### luaL_buffsub
#### luaL_callmeta
#### luaL_checkany
#### luaL_checkinteger
#### luaL_checklstring
#### luaL_checknumber
#### luaL_checkoption
#### luaL_checkstack
#### luaL_checkstring
#### luaL_checktype
#### luaL_checkudata
#### luaL_checkversion
#### luaL_dofile
#### luaL_dostring
#### luaL_error
#### luaL_execresult
#### luaL_fileresult
#### luaL_getmetafield
#### luaL_getmetatable
#### luaL_getsubtable
#### luaL_gsub
#### luaL_len
#### luaL_loadbuffer
#### luaL_loadbufferx
#### luaL_loadfile
#### luaL_loadfilex
#### luaL_loadstring
#### luaL_newlib
#### luaL_newlibtable
#### luaL_newmetatable
#### luaL_newstate
#### luaL_openlibs
#### luaL_opt
#### luaL_optinteger
#### luaL_optlstring
#### luaL_optnumber
#### luaL_optstring
#### luaL_prepbuffer
#### luaL_prepbuffsize
#### luaL_pushfail
#### luaL_pushresult
#### luaL_pushresultsize
#### luaL_ref
#### luaL_requiref
#### luaL_setfuncs
#### luaL_setmetatable
#### luaL_testudata
#### luaL_tolstring
#### luaL_traceback
#### luaL_typeerror
#### luaL_typename
#### luaL_unref
#### luaL_where





### standard library
#### luaopen_base
#### luaopen_coroutine
#### luaopen_debug
#### luaopen_io
#### luaopen_math
#### luaopen_os
#### luaopen_package
#### luaopen_string
#### luaopen_table
#### luaopen_utf8





### constants
#### LUA_ERRERR
#### LUA_ERRFILE
#### LUA_ERRMEM
#### LUA_ERRRUN
#### LUA_ERRSYNTAX
#### LUA_HOOKCALL
#### LUA_HOOKCOUNT
#### LUA_HOOKLINE
#### LUA_HOOKRET
#### LUA_HOOKTAILCALL
#### LUAL_BUFFERSIZE
#### LUA_MASKCALL
#### LUA_MASKCOUNT
#### LUA_MASKLINE
#### LUA_MASKRET
#### LUA_MAXINTEGER
#### LUA_MININTEGER
#### LUA_MINSTACK
#### LUA_MULTRET
#### LUA_NOREF
#### LUA_OK
#### LUA_OPADD
#### LUA_OPBAND
#### LUA_OPBNOT
#### LUA_OPBOR
#### LUA_OPBXOR
#### LUA_OPDIV
#### LUA_OPEQ
#### LUA_OPIDIV
#### LUA_OPLE
#### LUA_OPLT
#### LUA_OPMOD
#### LUA_OPMUL
#### LUA_OPPOW
#### LUA_OPSHL
#### LUA_OPSHR
#### LUA_OPSUB
#### LUA_OPUNM
#### LUA_REFNIL
#### LUA_REGISTRYINDEX
#### LUA_RIDX_GLOBALS
#### LUA_RIDX_MAINTHREAD
#### LUA_TBOOLEAN
#### LUA_TFUNCTION
#### LUA_TLIGHTUSERDATA
#### LUA_TNIL
#### LUA_TNONE
#### LUA_TNUMBER
#### LUA_TSTRING
#### LUA_TTABLE
#### LUA_TTHREAD
#### LUA_TUSERDATA
#### LUA_USE_APICHECK
#### LUA_YIELD
# C++调用Python

> Author: Sylvie233
>
> Date: 23/5/21

[TOC]

## 基础介绍

将python当成一个库来调用

`Python.h`、`python39.lib`





## 核心内容

```
<Python.h>:
	PyObject:
	Py_BuildValue():
	Py_Finalize():
	Py_Initialize():
	Py_IsInitialized():
	PyArg_Parse(): PyObject值获取
		i: 整型
		s: 字符串
	PyCallable_Check():
	PyEval_CallObject(): 实例化类
	PyImport_ImportModule():
	PyObject_CallObject(): 调用函数
	PyObject_GetAttrString():
	PyRun_SimpleString():
	PyTuple_New(): 元组，用来传递参数
	PyTuple_SetItem():
```





### python函数

1. 初始化python接口
2. 初始化python系统文件路径
3. 调用python文件名
4. 获取函数对象
5. 调用函数对象
6. 结束python接口初始化










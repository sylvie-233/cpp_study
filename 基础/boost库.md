# Boost库

Sylvie233的C++学习~~~

> Author: Sylvie233
>
> Date: 2022/12/28

[TOC]



## 基础介绍



## Boost库

### \<boost/archive/text_oarchive.hpp>

### \<boost/archive/text_iarchive.hpp>

#### access

```
boost::serialization::access:
	
```



#### text_iarchive

```
boost::archive::text_iarchive:
```



#### text_oarchive

```
boost::archive::text_oarchive:
```







### \<boost/array.hpp>





### \<boost/asio.hpp>

#### async_connect

#### async_read

#### async_write

#### buffer

```
boost::asio::buffer:
	data():
```



#### connect

#### deadline_timer

```
boost::asio::deadline_timer:
    async_wait():
    cancel():
    expires_at():
    wait():

```



#### error

```
boost::asio::error:
    eof:
	operation_aborted:
```





#### io_service

```
boost::asio::io_service:
	post():
	reset():
	run():
	stopped():
	strand:
		post():
		wrap():
```



#### ip

```
boost::asio::ip:
	tcp:
		acceptor:
			accept():
			async_accept():
			get_io_service():
		endpoint:
		resolver:
			iterator:
			query:
			resolve():
		socket:
			async_read_some():
			close():
        	read_some():
        v4:
```



#### placeholders

```
boost::asio::placeholders:
	bytes_transferred:
	error:
	 
```



#### read



#### system

```
boost::system:
	error_code:
```



#### write



### \<boost/asio/steady_timer.hpp>

#### steady_timer

```
boost::asio::steady_timer:
	expires_from_now():
	wait():
```





### \<boost/bind.hpp>

#### bind



### \<boost/date_time/posix_time/posix_time.hpp>

#### posix_time

```
boost::posix_time:
	seconds():
	
```





### \<boost/log/core.hpp>

### \<boost/log/expressions.hpp>

### \<boost/log/trivial.hpp>

#### BOOST_LOG_TRIVIAL





### \<boost/property_tree/ptree.hpp>

### \<boost/property_tree/json_parser.hpp>

#### ptree

```
boost::property_tree::ptree:
	get<T>():
	put():
```

#### read_json

#### write_json
# HTTP协议基础

## HTTP请求过程
	1. 事务： 一次完整请求和响应，即不允许只有请求没有响应的情况
	2. 报文： 分为请求报文(request message)和响应报文(response message)

> HTTP工作在应用层，无需考虑数据包错误(丢包，乱序等),传输层

	一次网络请求的步骤：
	a. 浏览器从URL中解析出服务器主机名
	b. 通过DNS将服务器主机名称解析成对应的IP地址
	c. 从URL中解析出对应的端口号(没有则为默认的端口)
	d. 建立到Web服务器的TCP连接
	e. 向服务器发送HTTP请求报文
	f. 服务器返回响应报文
	g. 关闭连接，浏览器显示文档
>使用Telnet 可以直接打开TCP链接，可以手动发送请求

`隧道`（tunnel）:HTTP连接建立起来后对原始数据进行盲转发（不会窥探数据），常用的https使用在http上传输ssl(安全套接字层)流量的

## URL与资源
### URL组成
	协议：【用户名】+【密码】+主机+端口+路径+参数+查询+片段
	查询是？连接的参数
	片段 通过#分割

	URL：统一资源定位符
	URI：统一资源标志符
	URN：统一资源名
### 相对URL
相对URL转换成绝对URL的算法

### URL编码
	编码机制：将特殊字符的ascii码转成16进制，然后在前面添加%
	空格		--->	32（0x20） --->	%20
		
### URL保留字符

	一些转义字符和特殊字符，包括服务端程序限制的特殊字符
	
## HTTP报文
### 报文的组成
	start line	:	起始行		HTTP/1.1 200 OK	 CRLF换行
	header		:	首部			Content-type: text/plain CRLF换行
	body		:	主体			hello,world	可为文本，二进制，空
	请求报文格式：
	<method> <request-URL>	<version>
	<headers>
		注意这儿有个空行
	<entity-body>
	
	响应报文格式：
	<version> <status> <reason-phrase>
	<headers>
		注意这儿有个空行
	<entity-body>
	
### HTTP请求方法

	GET			从服务器获取内容		
	HEAD		获取文档头部
	POST		提交处理数据
	PUT			存储内容
	TRACE		追踪报文
	OPTIONS		查询服务器哪些方法
	DELETE		删除文档
	
### HTTP状态码

	范围			已用					分类
	100~199		100~101				信息提示
	200~299		200~206				成功
	300~399		300~305				重定向
	400~499		400~415				客户端错误
	500~599		500~505				服务器错误
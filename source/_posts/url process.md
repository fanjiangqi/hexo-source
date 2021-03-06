---
title: 面试题： url请求整个过程
date: 2017-09-01 22.06.00
tags: [网络,面试]
keywords: http, url请求
---

> 一个很常见的面试题：url请求的整个过程。
> 但如何答好，然面试官满意还是有一点难度的。我觉得主要是让面试官知道你了解TCP，IP，HTTP协议，dns解析这些基础知识。

1. 域名解析，用户输入url域名后，通过DNS服务把得到访问域名的ip地址。
具体：浏览器所在主机向本地DNS服务器发送域名查询报文，本地DNS服务器把请求转发给根服务器（DNS服务器分三种：根服务器，顶级DNS服务器，权威DNS服务器），根服务器通过判断域名后缀com等，返回给本地服务器对应的顶级域名服务器的ip地址，本地服务器发送请求到顶级域名服务器，顶级域名服务器通过判断，返回权威域名服务器ip地址，本地服务器再发送查询请求到权威域名服务器，最后得到请求域名对应的ip地址，本地服务器把ip地址响应报文发送给客户端主机。这里的查询过程是包含递归查询和迭代查询的，客户端主机发送给本地服务器的查询是递归查询，而后面的三个查询是迭代查询。
2. 封装HTTP请求
	浏览器把请求封装为HTTP报文，其中包括：请求的方法GET/PUT，请求路径，请求主机名，客户端的一些信息等。
3. 建立连接，通过TCP三次握手建立连接。
在应用层和传输层之间，更准确地讲是在浏览器进程和操作系统提供的TCP服务程序之间，有一个很重要的东西叫做套接字（Socket）。套接字的作用是实现传输层的多路复用和多路分解。TCP套接字是由一个四元组（源IP地址、源端口号、目的IP地址和目的端口号）来标识的在应用层可以同时运行多个进程，每个进程都需要通过传输层来收发分组，而传输层的TCP进程只有一个，当TCP进程收到一个分组后，该怎么确定应该转发给哪个进程呢？答案是通过套接字，这就是多路分解。同样的道理，多路复用就是进程将分组通过各自的套接字转发给传输层。
4. 发送请求
请求在“三次握手”的第三次“握手”就发送出去了。用户数据存储在TCP报文断的用户数据处，详见TCP报文段格式。
5. 路由寻址
此处请求传送到网络层，网络层最重要的功能是路由选择。通过录用选择，把数据传送到目标ip主机。
6. 关闭连接
 目标主机收到了请求后，自底向上地对该请求进行处理。链路层把数据报传给网络层，网路层将TCP数据段通过对应的Socket传给应用程序。应用程序处理请求后产生一个应答的HTTP报文，又经过了一层层的封装、一跳跳的传输到达了源主机。当一次请求传输完成后，目标主机需要通过TCP四次握手关闭连接。
 7. 客户端浏览器把得到的数据渲染给用户

---
其中需要重点更细理解的是：路由寻址。如何实现路由寻找？
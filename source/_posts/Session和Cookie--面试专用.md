---
title: Session和Cookie--面试专用 
date: 2017-08-28 16.30.00
tags: [技术,网络]
keywords: session, cookie
---

> 面试中经常会问道，session和cookie的区别，通常心里都有一个答案，但如何回答的让面试官满意，还是需要好好斟酌。所以，记录下来我的思考，以后面试直接拿来主义。

1. 首先最重要的点，**cookie和session都是用来跟踪会话的机制。cookie是为了弥补HTTP协议无状态的不足而产生的**。
2. cookie是存储在客户端浏览器中的，session是存储在服务器端的。
3. cookie是不可跨域的（有setDomain()和setPath()属性）
4. session通过名为JSESSIONID的cookie来作为标识

### 跨域访问
> 面试中经常会问到，不同域名如何实现跨域共享。
例如：a.google.com 和b.google.com 如何共享登录信息（单点登录）

主要通过cookie的setDomain("*.google.com")属性来实现。
> 再深一点，通过上面方式实现跨域共享cookie，但是一级域名和二级域名不能实现session共享，如何解决？

思路：
1. 登录一级域名时，会保存一个JSESSIONID到cookie中
2. 访问二级域名时，由会重新生成一个JSESSIONID到cookie中
解决方法：
1. 把第一次登录的生成的JSESSIONID存储到一个共享域的cookie中
2. 访问二级域名时，把JSESSIONID设置为一级域名的JSESSIONID值，即存储在共享cookie中的值

这样就实现了，一级域名和二级域名下共享一个session。
# tinyhttpd



[toc]

## 1 HTTP请求与响应

**HTTP请求**

HTTP请求报文由三个部分组成：

请求行、请求头、请求体



例如：

![image-20210615200308176](C:\Users\Lavoie\AppData\Roaming\Typora\typora-user-images\image-20210615200308176.png)



* GET和POST是最常见的HTTP方法，其他的还有DELETE、HEAD、OPTIONS、PUT、TRACE

* 报文头包含若干属性，格式为`属性名:属性值`，服务端据此获得客户端的信息

* 报文体将一个页面表单中的组件值通过`param1=value1&param2=value2`的键值对形式编码成一个格式化串，它承载多个请求参数的数据。

  除了报文体可以传递请求参数，请求URL也可以通过类于“/chapter15/user.html? param1=value1&param2=value2”的方式传递请求参数。
  

**HTTP响应**

HTTP响应报文由三部分组成：

响应行、响应头、响应体



例如：

![image-20210615201029096](C:\Users\Lavoie\AppData\Roaming\Typora\typora-user-images\image-20210615201029096.png)



响应状态码：

1xx 消息，一般是告诉客户端，请求已经收到了，正在处理，别急…
2xx 处理成功，一般表示：请求收悉、我明白你要的、请求已受理、已经处理完成等信息.
3xx 重定向到其它地方。它让客户端再发起一个请求以完成整个处理。
4xx 处理发生错误，责任在客户端，如客户端的请求一个不存在的资源，客户端未被授权，禁止访问等。
5xx 处理发生错误，责任在服务端，如服务端抛出异常，路由出错，HTTP版本不支持等。



## 2 GET、POST

GET：用于获取信息，是无副作用的，幂等的（执行一次与连续执行多次的效果是一样的，服务器的状态也是一样的），可缓存

POST：用于修改服务器上的数据，有副作用，非幂等，不可缓存



一般GET的参数写在URL里面，而POST的参数写在Body里面，这样看POST稍微安全一点，但是从传输的角度看，它们都是不安全的，因为HTTP在网络上是明文传输的，要想安全传输，要使用HTTPS。



## 3 tinyhttpd

**Overview**

![image-20210616215742638](C:\Users\Lavoie\AppData\Roaming\Typora\typora-user-images\image-20210616215742638.png)

**执行**

1

![image-20210616220001993](C:\Users\Lavoie\AppData\Roaming\Typora\typora-user-images\image-20210616220001993.png)

2

![image-20210616220105586](C:\Users\Lavoie\AppData\Roaming\Typora\typora-user-images\image-20210616220105586.png)
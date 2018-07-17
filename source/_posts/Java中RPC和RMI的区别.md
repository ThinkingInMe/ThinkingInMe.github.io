---
title: Java中RPC和RMI的区别浅析
date: 2018-06-02 21:12:41
categories: '分布式' 
---
# Java中RPC和RMI的区别

> RPC： 远程过程调用协议（Remote Proceduce Call Port），通过网络从远程计算机上请求调用服务。

* 客户端暴露接口，传递参数
* 通过客户端网络发送请求
* 服务端接受消息并处理远程服务
* 执行完毕返回结果到客户端

> RMI：远程方法调用协议（Remote Method Invocation），能在客户端Java虚拟机上调用其他Java虚拟机的方法。

<!-- more -->

* 客户端代理对象调用服务端代理对象

```java
服务端远程接口继承类：UnicastRemoteObject-->RemoteObject-->Remote/Serializable
1、服务端通过LocateRegistry.createRegistry(1099)创建一个注册中心，通过Naming.rebind("name", object)映射远程对象的引用；
2、客户端通过Naming.lookup("name")获取该Object对象；
```



#  适用的语言范围

* RMI 仅限于Java语言
* RPC是网络服务协议，与操作系统和语言无关


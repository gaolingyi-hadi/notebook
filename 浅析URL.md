# 浅析 URL
## URL 包含哪几部分，每部分分别有什么作用
![](https://user-gold-cdn.xitu.io/2020/6/12/172a41e7fe902def?w=1628&h=532&f=png&s=431701)
URL指的是统一资源定位符（Uniform Resource Locator）。URL包含协议、域名或IP、端口号、路径、查询参数、锚点。

* 协议:表明了浏览器必须使用何种协议，HTTP或HTTPS。
* 域名或端口:表明正在请求哪个Web服务器。
* 端口:表名访问Web服务器上的哪个服务。HTTP协议的标准端口，HTTP为80，HTTPS为443。
* 路径:用来定位文件位置。
* 查询参数: 参数是用 & 符号分隔的键/值对列表
* 锚点: 用来定位当前内容的不同位置,并且不会被服务器接收到

## DNS 的作用是什么，`nslookup` 命令怎么用
DNS （Domain Name System ）用来解析域名查出IP地址。

`nslookup`可以查询DNS的记录，使用方法是`nslookup "域名或ip"`
## IP 的作用是什么，ping 命令怎么用

ip的作用是**实现主机与主机之间的通信**

`ping`命令可以指定机器通讯一下来查看网络情况,使用方法是`ping "域名或ip"`
## 域名是什么，分别哪几类域名
域名就是ip的别称

通用顶级域名按后缀分，顶级域名，
* .com(顶级域名)
* xxx.com （二级域名）
* i.xxx.com （三级域名)

依照用途又可称为通用顶级域名，分别是.com、.net、.org、.int、.edu、.gov、.mil。
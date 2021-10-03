#### 应用层常用协议

###### HTTP协议

* 服务器端口：80

###### SMTP协议

* 端口：25
* `Email`消息只能包含7位`ASCII`码
* 持久性连接

###### POP协议

* 有“下载并删除”和“下载并保留”模式
* `POP3`是无状态的

###### IMAP协议

* 所有消息统一保存在服务器
* 支持跨会话的用户状态

###### FTP协议

* 服务器端口：21

###### DNS

**资源记录**

`RR=(name, value, type, ttl)`

根据`type`字段，有不同的记录含义

* `type=A`

	`name`为主机域名

	`value`为IP地址

* `type=NS`

	`name`为域

	`value`为该域的权威域名解析器的主机域名

* `type=CNAME`

	`name`为主机域名

	`value`为IP地址

* `type=MX`

#### 主定理求解递归式

对于递推关系式
$$
T(n)=aT(\frac{n}{b})+f(n)
$$

* 若存在$\epsilon>0$，使得$f(n)=O(n^{\log_ba-\epsilon})$，则$T(n)=\Theta(n^{\log_ba})$；
* 若$f(n)=\Theta(n^{\log_ba})$，则$T(n)=\Theta(n^{\log_ba}\log n)$；
* 若存在$\epsilon>0$，使得$f(n)=\Omega(n^{\log_ba+\epsilon})$，且存在$c<1,n_0>0$，使得当$n>n_0$时，$af(\frac{n}{b})\leq cf(n)$，则$T(n)=\Theta(f(n))$

将函数$f(n)$与$n^{\log_ba}$进行比较，较大者决定递归式的解

* 若$n^{\log_ba}$更大，如情况一，则解为$T(n)=\Theta(n^{\log_ba})$；
* 若$f(n)$更大，如情况三，则解为$T(n)=\Theta(f(n))$；
* 若两个函数相等，如情况二，则解为$T(n)=\Theta(n^{\log_ba}\log n)$；


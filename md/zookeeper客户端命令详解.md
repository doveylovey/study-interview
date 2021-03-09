# zookeeper客户端命令详解

### zkCli.sh -server host:port：用zkClient连接到指定zookeeper服务器
如：./zkCli.sh -server localhost:2181

### help命令：用于查询客服端所支持的所用的命令
### close命令：用于关闭与zookeeper服务器的连接

### connect命令：切换连接的zookeeper服务器，与close命令配合使用可以连接或者断开zookeeper服务器
如：connect 127.0.0.1:2181

### get命令：用于获取节点的信息。注意节点的路径必须是以/开头的绝对路径
如：get /

```
cZxid = 0x0	# 该节点创建时的zxid
ctime = Thu Jan 01 08:00:00 CST 1970	# 该节点创建时间
mZxid = 0x0	# 该节点最近一次更新时的zxid
mtime = Thu Jan 01 08:00:00 CST 1970	# 该节点最近一次更新的时间
pZxid = 0x0	# 该节点最近一次更新的zxid
cversion = -1	# 子节点数据更新次数
dataVersion = 0	# 该节点数据更新次数，每次修改内容版本都会增加
aclVersion = 0	# 该节点ACL(授权信息)的更新次数
ephemeralOwner = 0x0	# 如果该节点为临时节点，ephemeralOwner值表示与该节点绑定的session id；如果该节点不是临时节点，ephemeralOwner值为0
dataLength = 0	# 该节点存储的数据长度
numChildren = 1	# 该节点的子节点个数
```

`

### stat命令：用于查看节点的状态信息
如：stat /
该命令的结果参数说明同get命令

### set命令：用于设置节点的数据
如：set /user hello

### ls命令:用于获取路径下的节点信息。注意路径为绝对路径
如：ls /user

### ls2命令:是ls命令的增强版，比ls命令多输出本节点信息
如：ls2 /user

### listquota命令:用于显示配额
如：listquota /user

### setquota命令:用于设置节点个数以及数据长度的配额
如：setquota –n 4 /zookeeper/node # 设置/zookeeper/node子节点个数最大为4
如：setquota –b 100 /zookeeper/node # 设置/zookeeper/node节点长度最大为100

### delquota命令：用于删除配额，-n为子节点个数，-b为节点数据长度
如：delquota –n 2

### history命令：用于列出最近的命令历史，可以和redo配合使用
如：history

```
10 - ls2 /zookeeper
11 - get /
12 - set /user hello
13 - create /user
14 - set /user hello
15 - create /user "hello"
16 - get /user
17 - set /user "hello123456"
18 - ls /user
19 - ls2 /user
20 - history
```



### redo命令：用于再次执行某个命令，常与history配合使用。使用方式为redo cmdId
如：redo 20

### create命令:用于创建节点，其中-s为顺序充点，-e临时节点　
如：create /user/node1 "test_create" world:anyone:r

### delete命令：用于删除节点
如：delete /user/node1

### addauth命令:用于节点认证
如：addauth digest username:password

### setAcl命令：用于设置节点Acl
Acl由三部分构成：1为scheme，2为user，3为permission，一般情况下表示为scheme:id:permissions

### getAcl命令：获取节点的Acl
如：getAcl /user/node1

=====>scheme和id
world: 它下面只有一个id, 叫anyone, world:anyone代表任何人，zookeeper中对所有人有权限的节点就是属于world:anyone的
auth: 它不需要id, 只要是通过authentication的user都有权限（zookeeper支持通过kerberos来进行authencation, 也支持username/password形式的authentication)
digest: 它对应的id为username:BASE64(SHA1(password))，它需要先通过username:password形式的authentication
ip: 它对应的id为客户机的IP地址，设置的时候可以设置一个ip段，比如ip:192.168.1.0/16, 表示匹配前16个bit的IP段
super: 在这种scheme情况下，对应的id拥有超级权限，可以做任何事情(cdrwa)
=====>permissions
CREATE(c): 创建权限，可以在在当前node下创建child node
DELETE(d): 删除权限，可以删除当前的node
READ(r): 读权限，可以获取当前node的数据，可以list当前node所有的child nodes
WRITE(w): 写权限，可以向当前node写数据
ADMIN(a): 管理权限，可以设置当前node的permission

### sync命令：用于强制同步，由于请求在半数以上的zk server上生效就表示此请求生效，那么就会有一些zk server上的数据是旧的。sync命令就是强制同步所有的更新操作。

### printwatchers命令：用于设置和显示监视状态，值为on或则off

### quit命令：退出客户端

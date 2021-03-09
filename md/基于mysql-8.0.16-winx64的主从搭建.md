1、主 my.ini 文件内容：
[mysqld]
# 主库和从库需要不一致
server-id=1
log-bin=mysql-bin
# 同步的数据库
binlog-do-db=master-slave
# 不需要同步的数据库
binlog-ignore-db=mysql
# 设置3366端口
port=3366
# 设置mysql的安装目录
basedir=E:\Develops\MySQL\mysql-8.0.16-winx64-master
# 设置mysql数据库的数据的存放目录
datadir=E:\Develops\MySQL\mysql-8.0.16-winx64-master\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。
max_connect_errors=10
# 服务端使用的字符集默认为UTF8
character-set-server=UTF8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
#mysql_native_password
default_authentication_plugin=mysql_native_password

[mysql]
# 设置mysql客户端默认字符集
default-character-set=UTF8

[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3366
default-character-set=UTF8

2、从 my.ini 文件内容：
[mysqld]
# 主库和从库需要不一致
server-id=2
log-bin=mysql-bin
# 同步的数据库
binlog-do-db=master-slave
# 不需要同步的数据库
binlog-ignore-db=mysql
# 设置3367端口
port=3367
# 设置mysql的安装目录
basedir=E:\Develops\MySQL\mysql-8.0.16-winx64-slave
# 设置mysql数据库的数据的存放目录
datadir=E:\Develops\MySQL\mysql-8.0.16-winx64-slave\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。
max_connect_errors=10
# 服务端使用的字符集默认为UTF8
character-set-server=UTF8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
#mysql_native_password
default_authentication_plugin=mysql_native_password

[mysql]
# 设置mysql客户端默认字符集
default-character-set=UTF8

[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3367
default-character-set=UTF8

3、安装 mysql 服务器：
初始化mysql：
mysqld --defaults-file=E:\Develops\MySQL\mysql-8.0.16-winx64-slave\my.ini --initialize --console
安装mysql服务：
mysqld --install MySQL3367-slave --defaults-file="E:\Develops\MySQL\mysql-8.0.16-winx64-slave\my.ini"
注意修改下注册表：
找到 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MySQL3367-slave,修改ImagePath参数，更正MySQL3367-slave服务相关路径
启动服务：
net start MySQL3367-slave
root账户登录mysql：
mysql -u root -p --protocol=tcp --host=localhost --port=3367
修改密码：
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
开放权限：
flush privileges;

4、主从配置
mysql8在主服务器上创建复制用户并授权：
create user slave@'%' identified  by 'root';
ALTER USER 'slave'@'%' IDENTIFIED WITH mysql_native_password BY 'root';
grant all privileges on *.* to slave@'%' with grant option;
flush privileges;

查看当前服务器的server-id：
show variables like 'server_id';

查看主服务器状态：
show master status;

stop slave;
change master to master_host='localhost',master_port=3366,master_user='slave',master_password='slave',master_log_file='mysql-bin.000007',master_log_pos=379;
start slave;

查看从服务器状态：
show slave status\G;
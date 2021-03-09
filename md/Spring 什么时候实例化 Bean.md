###################################
Spring 什么时候实例化 Bean？首先要分2种情况：

第一：如果使用 BeanFactory 作为 Spring Bean 的工厂类，则所有的 Bean 都是在第一次使用时实例化的(不管 Bean 是否实现了 FactoryBean)。
第二：如果使用 ApplicationContext 作为 Spring Bean 的工厂类，则又分为以下几种情况：
(1)、如果 Bean 的 scope 是 singleton 的，并且 lazy-init 为 false(默认是 false，所以可以不用设置)，则 ApplicationContext 启动时就实例化该 Bean，并将实例化的 Bean 放在一个 Map 结构的缓存中，下次再使用该 Bean 时直接从这个缓存中取(但如果该 Bean 实现了 FactoryBean，则 ApplicationContext 启动时会先实例化对应的 FactoryBean，当第一次使用该 Bean 时再通过 FactoryBean 的 getObject 方法实例化 Bean)。
(2)、如果 Bean 的 scope 是 singleton 的，并且 lazy-init 为 true，则该 Bean 的实例化是在第一次使用时。
(3)、如果 Bean 的 scope 是 prototype 的，则该 Bean 的实例化是在第一次使用时。


###################################
开放性的设计系统问题：有一家生产奶酪的厂家，每天需要生产100000份奶酪卖给超市，通过一辆送货车发货，送货车辆每次送100份。
厂家有一个容量为1000份的冷库用于奶酪保鲜，生产的奶酪需要先存放在冷库，运输车辆从冷库取货。
厂家有三条生产线，分别是：牛奶供应生产线、发酵剂制作生产线、奶酪生产线。生产每份奶酪需要2份牛奶和1份发酵剂。
请设计生产系统。


###################################
Map<String, Config> configMap = configService.mapConfigByKeys(new ArrayList<String>() {{
	this.add(Config.Constant.AGENT_MAX_WITHDRAW_MONEY);
	this.add(Config.Constant.AGENT_MIN_WITHDRAW_MONEY);
	this.add(Config.Constant.AGENT_FEE_WITHDRAW_MONEY);
}});
@Override
public Map<String, Config> mapConfigByKeys(List<String> keys) {
	List<Config> list = configMapper.listConfigByKeys(keys);
	Map<String, Config> configMap = list.stream()
	.collect(Collectors.toMap(config -> config.getTermKey(), config -> config));
	return configMap;
}
<select id="listConfigByKeys" parameterType="list" resultType="com.xd.internat.user.intf.entity.Config">
	SELECT `code`, term_key AS termKey, term_value AS termValue, remark
	FROM xd_config
	WHERE term_key IN
	<foreach collection="list" item="item" open="(" close=")" separator=",">
		#{item}
	</foreach>
</select>


###################################
db.system.users.find().pretty()
db.auth("admin","admin")
db.dropUser("admin")
db.createUser({user: "admin", pwd: "admin", roles: [{role: "root", db: "admin"}]})
db.createUser({user: "admin", pwd: "admin", roles: [{role: "readWriteAnyDatabase", db: "test"}]})
db.createUser({user: "admin", pwd: "admin", roles: [{role: "readWrite", db: "read_write"}]})
db.course.insert({
	title: 'MongoDB 教程', 
    description: 'MongoDB 是一个 Nosql 数据库',
    by: '菜鸟教程',
    url: 'http://www.runoob.com',
    tags: ['mongodb', 'database', 'NoSQL'],
    likes: 100
})


###################################
参考：https://www.cnblogs.com/liuliuyan/p/10945398.html、https://www.cnblogs.com/ifme/p/11796924.html

初始化：
mysqld --defaults-file=D:\database\MySQL\mysql-5.7.28-winx64-master\my.ini --initialize --user=mysql --console
安装服务，名称为 MySQL57-3337-master：
mysqld --install MySQL57-3337-master --defaults-file="D:\database\MySQL\mysql-5.7.28-winx64-master\my.ini"

mysqld --defaults-file=D:\database\MySQL\mysql-5.7.28-winx64-slave1\my.ini --initialize --user=mysql --console
mysqld --install MySQL57-3338-slave1 --defaults-file="D:\database\MySQL\mysql-5.7.28-winx64-slave1\my.ini"

mysqld --defaults-file=D:\database\MySQL\mysql-5.7.28-winx64-slave2\my.ini --initialize --user=mysql --console
mysqld --install MySQL57-3339-slave2 --defaults-file="D:\database\MySQL\mysql-5.7.28-winx64-slave2\my.ini"

启动服务：
net start MySQL57-3337-master
连接数据库，回车后输入初始化时生成的临时密码：
mysql -uroot -P3339 -p
修改密码：
set password=password("root");
刷新权限：
flush privileges;

主库执行：
show master status\G;
create user ms;
grant replication slave on *.* to ms@'%' identified by 'ms';
flush privileges;

从库1执行：
show slave status\G;
stop slave;
change master to master_host='127.0.0.1',master_port=3337,master_user='ms',master_password='ms',master_log_file='mysql-bin.000006',master_log_pos=154;
start slave;
show slave status\G;

从库2执行：
show slave status\G;
stop slave;
change master to master_host='127.0.0.1',master_port=3337,master_user='ms',master_password='ms',master_log_file='mysql-bin.000006',master_log_pos=154;
start slave;
show slave status\G;

主从恢复(注意修改 master_log_file 和 master_log_pos 以及其他配置信息)：
在主库上使用 show master status 获取 master_log_file 和 master_log_pos，再在从库上执行如下命令
stop slave;
change master to master_host='127.0.0.1',master_port=3337,master_user='ms',master_password='ms',master_log_file='mysql-bin.000001',master_log_pos=0;
start slave;


###################################
Spring 事件机制
参考：https://www.cnblogs.com/xinde123/p/8918714.html
https://www.cnblogs.com/vettel0329/p/11269733.html


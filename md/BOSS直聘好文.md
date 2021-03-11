## @NotNull、@NotEmpty、@NotBlank 三个注解区别

- @NotNull：不能为null，但可以为empty(""," “,” ")，一般用在基本数据类型的非空校验上，而且被其标注的字段可以使用 @size/@Max/@Min对字段数值进行大小的控制
- @NotEmpty：不能为null，而且长度必须大于0(" “,” ")，一般用在集合类上面
- @NotBlank：这玩意只能作用在接收的String类型上，注意是只能，不能为null，而且调用trim()后，长度必须大于0

## 精选推荐
- 面试被问线程池，真香：https://www.cnblogs.com/guofuangela/p/14381030.html
- 年初敖丙天猫面试真题：如果设计一个数据库？我人傻了：https://new.qq.com/omn/20201214/20201214A02G4800.html
- Spring Boot 面试，一个问题你就答不上来了：https://blog.csdn.net/chen801090/article/details/101454624
- 外婆问我：什么是双亲委派原则：https://my.oschina.net/javaFamily/blog/4967284
- 字节二面：优化 HTTPS 的手段，你知道几个：https://blog.csdn.net/sufu1065/article/details/113409525
- 阿里巴巴Druid，轻松实现MySQL数据库加密：https://blog.csdn.net/g6U8W7p06dCO99fQ3/article/details/114464555
- 判断相等_回文字符串判断的3种方法：https://blog.csdn.net/weixin_28705087/article/details/112656340
- 你还在手写 CRUD？试试 MybatisGenerator，再也不用加班了：https://www.cnblogs.com/javastack/p/14411104.html
- Redis 性能优化的 13 条军规！史上最全：https://blog.csdn.net/sufu1065/article/details/105146285/
- 为什么SpringBoot的 jar 可以直接运行：https://blog.csdn.net/weixin_44337261/article/details/105897860
- 面试官问：如果让你写一个配置中心，说说你的设计思路？不要慌，看这个：https://blog.csdn.net/XingXing_Java/article/details/111085409
- 内存耗尽后Redis会发生什么：https://www.cnblogs.com/lonely-wolf/p/14403264.html
- Java面试必问：ThreadLocal终极篇：https://www.cnblogs.com/aobing/p/13382184.html
- 阿里面试：说说一致性读实现原理：https://blog.csdn.net/dreamhua927/article/details/110056340
- 面试 HTTP ，99% 的面试官都爱问这些问题：https://www.cnblogs.com/cxuanBlog/p/12735623.html
- 算法图解：如何判断括号是否有效：https://www.cnblogs.com/0591jb/p/13836331.html

## 面试集合
- 最常见的10种Java异常问题：https://blog.csdn.net/sufu1065/article/details/113667730
- 面试官：你说说互斥锁、自旋锁、读写锁、悲观锁、乐观锁的应用场景：https://www.cnblogs.com/xiaolincoding/p/13675202.html
- 什么是ZooKeeper：https://my.oschina.net/u/3777556/blog/3037221
- 这10道大厂Java面试题，我敢打赌90%的人都不会：https://www.cnblogs.com/hejunlin/p/12885050.html
- mysql的limit用法、逻辑分页和物理分页：https://blog.csdn.net/lvoelife/article/details/81943070
- 面试官：如何保证缓存一致性？一篇文章带你分析到位：https://blog.csdn.net/XingXing_Java/article/details/111567615
- 面试官：说说什么是单点登录？什么是SSO？什么是CAS：https://blog.csdn.net/Soar_M/article/details/112910872
- Spring Boot 面试，一个问题你就答不上来了：https://blog.csdn.net/chen801090/article/details/101454624
- 如何在面试中介绍自己的项目经验：https://www.cnblogs.com/JavaArchitect/p/7586949.html
- 阿里面试官问我Java线程和操作系统线程什么关系：https://blog.csdn.net/g6U8W7p06dCO99fQ3/article/details/113153033
- Java 中的 String 有没有长度限制：https://blog.csdn.net/csdnnews/article/details/106394295
- 进程之间究竟有哪些通信方式：https://blog.csdn.net/weixin_43226231/article/details/100112556
- 如何保障消息中间件 100% 消息投递成功？如何保证消息幂等性：https://www.cnblogs.com/tiancai/p/12187499.html
- 面试官：你了解大厂的接口设计原则么？就会curd的我当场自闭：https://aobing.blog.csdn.net/article/details/109604398
- 面试官：HashMap 为什么线程不安全：https://blog.csdn.net/qq_45076180/article/details/105650680
- 阿里最喜欢问的多线程顺序打印的5种解法：https://blog.csdn.net/sufu1065/article/details/109506906
- 面试官：你的项目是如何处理重复请求/并发请求的：https://blog.csdn.net/y0q2t57s/article/details/109792047

## 必会框架
- 3种时间格式化的方法，SpringBoot篇：https://blog.csdn.net/yiguang_820/article/details/108438509
- 你还在用分页？试试 MyBatis 流式查询，真心强大：https://blog.csdn.net/youanyyou/article/details/111188945
- SpringBoot集成Google开源图片处理框架，贼好用：https://blog.csdn.net/sufu1065/article/details/112211131
- 记一次大促期间JVM堆外内存泄漏故障排查记录：https://my.oschina.net/javaFamily/blog/4718646
- JVM必问知识点:类加载过程：https://www.pianshen.com/article/3653411891/
- 链表反转的两种实现方法，后一种击败了100%的用户：https://blog.csdn.net/csdnnews/article/details/109233980
- SpringBoot接口幂等性实现的4种方案：https://www.cnblogs.com/cqqfboy/p/14478237.html
- Java中的 Switch 是如何支持 String 的？为什么不支持 long：https://blog.csdn.net/weixin_36380516/article/details/113011269
- 了解JVM的结构，好在面试时吹牛：https://blog.csdn.net/qq_46388795/article/details/106586871
- 从 0 开始手写一个Tomcat，7 步搞定：https://blog.csdn.net/Walker_zmc/article/details/86664755
- 5种SpringBoot热部署方式，你用哪种：https://blog.csdn.net/weixin_39683021/article/details/111170445
- 笑话：大厂都在用的任务调度框架我能不知道吗：https://www.cnblogs.com/yinjihuan/p/12849787.html
- Java新特性：数据类型可以扔掉了：https://blog.csdn.net/weixin_36380516/article/details/109269135
- 一分钟带你玩转 Spring IoC：https://blog.csdn.net/weixin_38405253/article/details/105570945
- Springboot启动扩展点超详细总结，再也不怕面试官问了：https://blog.csdn.net/weixin_47067712/article/details/107002748
- 面试必杀技，讲一讲Spring中的循环依赖：https://blog.csdn.net/qq_41907991/article/details/107164508

## 数据库
- Redis的8大数据类型，写的真好：https://blog.csdn.net/sufu1065/article/details/110944495
- MySQL中，21个写SQL的好习惯：https://javazhiyin.blog.csdn.net/article/details/109505861
- 为什么阿里巴巴不建议MySQL使用Text类型：https://zhuanlan.zhihu.com/p/280021373
- 阿里 Mock 工具正式开源，干掉市面上所有 Mock 工具：https://www.jianshu.com/p/84dff2508600
- Redis中是如何实现分布式锁的：https://www.cnblogs.com/javazhiyin/p/11737403.html
- 使用 Redis 实现一个轻量级的搜索引擎，牛逼啊：https://blog.csdn.net/lianggzone/article/details/112597849
- URL 去重的 6 种方案：https://blog.csdn.net/qq_37217713/article/details/108525846
- 敖丙工作以来总结的大厂SQL调优姿势：https://database.51cto.com/art/202011/631904.htm
- 面试官不讲武德问我：为什么MySQL不建议使用delete删除数据：https://blog.csdn.net/qq_35190492/article/details/109735448
- Socket粘包问题的3种解决方案，最后一种最完美：https://www.cnblogs.com/vipstone/p/14239160.html
- MySQL索引凭什么能让查询效率提高这么多：https://www.cnblogs.com/aobing/p/13623703.html
- Intellij IDEA 阅读源码的 4 个绝技，我必须分享给你：https://blog.csdn.net/youanyyou/article/details/89368774
- 优秀程序员必备技能之如何高效阅读源码：https://blog.csdn.net/LiangGzone/article/details/113787486
- Spring Boot集成Redis，这个坑把我害惨了：https://blog.csdn.net/weixin_39829501/article/details/112650747
- 一口气搞懂MySQL索引所有知识点：https://mp.weixin.qq.com/s/faOaXRQM8p0kwseSHaMCbg


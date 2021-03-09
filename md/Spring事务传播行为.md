# Spring事务传播行为——为了解决业务层方法之间互相调用时的事务问题
当事务方法被另一个事务方法调用时，必须指定事务应该如何传播，因为方法可能继续在现有事务中运行，也可能开启一个新事务并在自己的事务中运行。Spring在org.springframework.transaction.TransactionDefinition接口中定义了如下几个表示传播行为的常量(三种七个)：
### 1、支持当前事务的情况
- int PROPAGATION_REQUIRED = 0：如果当前存在事务，则加入该事务；如果当前没有事务，则创建一个新的事务。
- int PROPAGATION_SUPPORTS = 1：如果当前存在事务，则加入该事务；如果当前没有事务，则以非事务的方式继续运行。
- int PROPAGATION_MANDATORY = 2：如果当前存在事务，则加入该事务；如果当前没有事务，则抛出异常。
### 2、不支持当前事务的情况
- int PROPAGATION_REQUIRES_NEW = 3：创建一个新的事务，如果当前存在事务，则把当前事务挂起。
- int PROPAGATION_NOT_SUPPORTED = 4：以非事务方式运行，如果当前存在事务，则把当前事务挂起。
- int PROPAGATION_NEVER = 5： 以非事务方式运行，如果当前存在事务，则抛出异常。
### 3、其他情况
- int PROPAGATION_NESTED = 6：如果当前存在事务，则创建一个事务作为当前事务的嵌套事务来运行；如果当前没有事务，则该取值等价于TransactionDefinition.PROPAGATION_REQUIRED。
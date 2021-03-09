Spring 事务回滚机制
====================================

在 Spring 应用中，方法上未加任何属性的 @Transactional 注解只能在抛出 RuntimeException 或 Error 时才会触发事务的回滚，常见的非 RuntimeException 是不会触发事务的回滚的。如果要在抛出非 RuntimeException 时也触发回滚机制，则需要我们在注解上添加 rollbackFor = { Exception.class } 属性。
注：以上事务回滚的前提是添加 @Transactional 注解的方法中不含有 try{...}catch(){...} 捕获异常，使得程序运行过程中出现异常能顺利抛出，从而触发事务回滚。

在实际开发中，我们往往需要在方法中进行异常的捕获，从而对异常进行判断，为客户端返回提示信息。但此时由于异常被捕获，导致事务的回滚没有被触发，进一步导致事务失败。下面提供几种解决方法：
### 1、遇到异常时事务自动回滚
```java
@Transactional(rollbackFor = Exception.class)
@Override
public void update() throws Exception {
	method1();
	// 假如操作数据库的 method2() 方法会抛出异常，则 method1() 方法中对数据库的操作会回滚
    method2();
}
```

### 2、使用 @Transactional 注解，抛出 @Transactional 注解默认识别的 RuntimeException。
方法上使用 @Transactional 注解，捕获到异常时在 catch 语句中抛出 RuntimeException。
```java
@Transactional
@Override
public void update() throws Exception {
	try{
		method();
	} catch(Exception e) {
		log.error("异常日志信息");
		throw new RuntimeException();
	}
}
```

### 3、使用 @Transactional(rollbackFor = { Exception.class })，抛出捕获到的非 RuntimeException。
方法上使用 @Transactional(rollbackFor = { Exception.class }) 注解声明事务回滚的异常类型，捕获到异常时在 catch 语句中直接抛出所捕获到的异常。
```java
@Transactional(rollbackFor = Exception.class)
@Override
public void update() throws Exception {
	try{
		method();
	} catch(Exception e) {
		log.error("异常日志信息");
		throw e;
	}
}
```

### 4、手动回滚异常
方法2、方法3在 catch(Exception e){...} 中抛出异常的方法都有个不足之处，就是不能在 catch(Exception e){...} 中存在 return 子句，所以可以设置手动回滚，当捕获到异常时，手动回滚，同时返回前台提示信息。
```java
@Transactional(rollbackFor = Exception.class)
@Override
public String update() throws Exception {
	try{
		method();
	} catch(Exception e) {
		log.error("异常日志信息");
		// 手动回滚事务
		TransactionAspectSupport.currentTransactionStatus().setRollbackOnly();
		return "失败！";
	}
	return "成功";
}
```

### 5、手动回滚部分异常
使用 Object savePoint = TransactionAspectSupport.currentTransactionStatus().createSavepoint(); 设置回滚点。
使用 TransactionAspectSupport.currentTransactionStatus().rollbackToSavepoint(savePoint); 回滚到 savePoint。
```java
@Transactional(rollbackFor = Exception.class)
@Override
public String update() throws Exception {
	method1();
	// 设置回滚点，只回滚以下异常
	Object savePoint = TransactionAspectSupport.currentTransactionStatus().createSavepoint();
	try{
		method2();
	} catch(Exception e) {
		log.error("异常日志信息");
		// 手工回滚异常，回滚到savePoint
		TransactionAspectSupport.currentTransactionStatus().rollbackToSavepoint(savePoint);
		return "失败！";
	}
	return "成功";
}
```


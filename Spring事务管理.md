PlatformTransactionManager:  平台事务管理器，spring 要管理事务，必须使用事务管理器

进行事务配置时，必须配置事务管理器

TransactionDefinition : 事务详情(事务定义，事务属性) spring用于确定事务具体详情。

例如： 隔离级别，是否只读，超时时间等

进行事务配置时，必须配置详情。 spring 将配置项封装到该对象实例。

TransactionStatus ： 事务状态 spring用于记录当前事务运行状态。例如：是否有保存点，事务是否完成。

spring 底层根据状态进行相应操作。

## PlatformTransactionManager 事务管理器

```
TransactionStatus getTransaction(TransactionDefinition var1)
```

事务管理器 通过"事务详情" 获得"事务状态"

```
void commit(TransactionStatus var1)
```

根据状态提交

```
void rollback(TransactionStatus var1)
```

根据状态回滚

## TransactionDefinition

```
String getName()
```

配置事务详情名称。一般方法名称。例如：save，add*等

```
boolean isReadOnly()
```

是否只读(增删改:读写，查询:只读)

```
int getTimeout()
```

获得超时时间

```
int getIsolationLevel()
```

隔离级别

```
int getPropagationBehavior()
```

传播行为

```
int TIMEOUT_DEFAULT = -1;
```

超时时间。默认值:-1. 使用数据库给定的超时时间

```
int ISOLATION_DEFAULT = -1;
int ISOLATION_READ_UNCOMMITTED = 1;
int ISOLATION_READ_COMMITTED = 2;
int ISOLATION_REPEATABLE_READ = 4;
int ISOLATION_SERIALIZABLE = 8;
```

隔离级别

## 传播行为

在两个业务之间如何共享事务。

### PROPAGATION_REQUIRED required 必须(重要)

支持当前事务，A如果有事务，B将使用该事务

如果A没有事务，B将创建一个新的事务

### PROPAGATION_SUPPORTS  supports 支持

支持当前事务，A如果有事务，B将使用该事务

如果A没有事务，B将以非事务执行

### PROPAGATION_MANDATORY mandatory 强制

支持当前事务，A如果有事务，B将使用该事务

如果A没有事务，B将抛异常

### PROPAGATION_REQUIRES_NEW require_new  必须新的(重要)

如果A有事务，将A的事务挂起，B创建一个新的事务

如果A没有事务，B将创建事务

### PROPAGATION_NOT_SUPPORTED  not_supported  不支持

如果A有事务，将A的事务挂起，B将以非事务执行

如果A没有事务，B将以非事务执行

### PROPAGATION_NEVER    never   不

如果A有事务，B将抛出 异常

如果A没有事务，B将以非事务执行

### PROPAGATION_NESTED nested 嵌套(重要)

A和B采用保存点机制，形成嵌套事务


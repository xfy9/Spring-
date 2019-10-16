spring底层使用TransactionTemplate 事务模板进行操作。

1. service 需要获得TransactionTemplate
2. spring 配置 TransactionTemplate 模板，并注入给service
3. 模板需要注入事务管理器
4. 配置事务管理器: DataSourceTransationManager
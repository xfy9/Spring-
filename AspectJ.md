# 介绍

AspectJ 是一个基于Java语言的AOP框架

Spring2.0 以后新增了对AspectJ切面表达式的支持

@AspectJ 是Aspect1.5新增功能，通过JDK5注解技术，允许直接在Bean类中定义切面。新版本Spring框架，建议使用AspectJ方式来开发AOP

# AspectJ 表达式

1. execution() 用于描述方法

   语法： execution（修饰符 返回值 包.类.方法(参数)throws 异常）

   - 修饰符：一般省略	

     - public:   公共方法
     - *:任意

   - 返回值: 不能省略

     - void : 返回值为空
     - String: 返回值为字符串
     - *:任意

   - 包[省略]

     - com.qust.parc: 固定包

     - com.qust.parc.*service: parc下面子包任意

       下的service

     - com.qust.parc.. prac包下面的所有子包(包括自己)

     - com.qust.parc.*service..  parc下面的任意子包，固定目录service，service目录任意包

   - 类[省略]

     - UserServiceImpl 指定类
     - *Impl ：以Impl结尾
     - User*： 以User开头

   - 方法:[不能省略]

     - addUser: 固定方法
     - add* : 以add开头
     - *Do： 以Do结尾
     - *：任意

   - 参数()

     - （）无参
     - （int） 一个整型
     - （int，int） 两个整形
     - （..）任意

   - throws，可省略，一般不写

# 通知类型

before ： 前置通知(应用：各种校验)

​	在方法执行前执行，如果通知抛出异常，阻止方法运行。

afterReturning：后置通知(应用: 常规数据处理)

​	方法正常返回后执行，如果方法中抛出异常，通知无法执行。

around：环绕通知(应用：十分强大，可以做任何事)

​	方法执行前后分别执行，可以阻止方法的执行

​	必须手动执行方法

afterThrowing： 抛出异常通知(应用：包装异常信息)

​	方法抛出异常后执行，如果方法没有抛出异常，无法执行

after：最终通知(应用：清理现场)

​	方法执行完毕后执行，无论方法中是否出现异常
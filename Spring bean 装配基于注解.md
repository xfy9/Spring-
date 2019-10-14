# Spring 注解

注解 : 就是一个类，使用@注解名称

开发中，使用注解取代xml配置文件

1. @Component 取代<bean class="">

   @Component("id") 取代<bean id="" class="">

   

2. web 开发，提供3个@Component 注解衍生注解

   @Repository: dao 层

   @ Service : service 层

   @ Controller : web 层

3. 依赖注入

   普通值 ： @Value("");

   引用值 ： 

   - 方式1：按照[类型]注入:

     - @Autowired

   - 方式2： 按照[名称]注入

     - @Autowired

       @Qualifier("名称")

     - @Resource("名称")

4. 生命周期

   初始化: @PostConstruct

   销毁 : @PreDestroy

5. 作用域

   @Scope("prototype") 多例

   6. 生命周期

      初始化： @PostConstruct

      销毁方法: @PreDestroy

### schema 命名空间

1. **命名空间声明**

默认 ： xmlns=“ ”   suchas : <标签名> ---> <bean>

显示:     xmlns: 别名=" "  <别名: 标签名>   ---> <context: ...>





2.**确定schema xsd 文件位置**

xsi:schemaLocation = "名称 位置 名称2 位置"


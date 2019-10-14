**spring配置文件:**

IOC ： <bean id="" class="">

DI : <bean><property name="" value=""| ref="">

**实例化方式:**

默认构造：<bean id="" class="">

静态工厂：<bean id="" class="工厂类" factory-method="静态方法"> 

实例工厂： <bean id="" factory-bean="工厂类" factory-method="工厂方法"> 

**作用域**：<bean id="" class="" scope="singleton|prototype">

**生命周期**: <bean id="" class="" init-method="" destroy-method="">

**后处理bean** : BeanProcessor接口,<bean class="注册">

对容器中所有的bean 都生效

**属性注入**:

​	构造方法注入：<bean><constructor-arg index= "" type="">

​    setter 方法注入: <bean><property>

​    p 命名空间： 简化property <bean p:属性名="普通值" p:属性名-ref="引用值">  注意声明命名空间

**集合**：

​	数组<array>

​	List<list>

​	Set <set>

​	Map <map><entry key="" value="">

​	Properties <props><pro key=""> ...value...

 

**核心api**

​	BeanFactory ：延迟实例化，第一次调用getBean

​	ApplicationContext 一般常用 ，功能更强

​     	ClassPathXmlApplicationContext 加载classpath.xml 文件

​    	 FileSystemXmlApplicationContext 加载指定盘符文件，    ServletConfig.getRealPath()

**注解**：见bean 装配.md



**注解和xml混合使用**

1. 将所有的bean都配置到 xml中

   <bean id="" class="">

2. 将所有的依赖都使用注解

   ​	@Autowired

   ​	默认不生效。为了生效，需要在xml配置：<context-annotation-config>

总结：

​	注解1 : <context:compoment-scan  base-packge="">

​	注解2: < context:annotation-config >

 1. 一般两个注解不同时使用

 2. 注解1 扫描含有注解(@Component 等)类，注入注解自动生效

    注解2 只有在xml和注解混合使用时，使注解生效。 


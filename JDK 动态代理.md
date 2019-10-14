# JDK 动态代理

JDK 动态代理对"装饰者" 设计模式 简化，使用前提，必须有接口。

1. 目标(委托)类：接口+实现类
2. 切面类：用于通知 
3. 工厂类: 编写工厂生产代理

   ## Proxy.newProxyIntance

参数1 : loader,类加载器，动态代理类，运行时创建，任何类都需要加载器将其加载到内存。

参数2: Class[] interfaces 代理类需要实现的所有接口

1. 目标类实例.getClass().getInterfaces(); 注意只能获得自己接口，不能获得父元素接口
2.  new Class[]{interface.class}

参数3：InvocationHandler 处理类，接口，必须进行实现类，一般采取匿名内部类

​	提供invoke方法，代理类的每一个方法执行时，都将调用一次invoke。

​		参数31：Object proxy ： 代理对象

​		参数32：Method method： 代理对象当前执行的方法的描述对象（反射）

​		参数33：Object[] args:方法实际参数					 
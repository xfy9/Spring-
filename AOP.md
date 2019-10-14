## AOP 实现原理

1. aop底层将采用代理机制进行实现
2. 接口+实现类 ：spring采用jdk的动态代理Proxy
3. 实现类 ：spring 采用cglib字节码增强

## AOP 术语

1. target ： 目标类，需要被代理的类，例如： UserService

2. Joinpoint： 连接点，所谓连接点是指那些可能被拦截到的方法。例如所有方法

3. PonitCut ：切入点，指已经被增强的连接点。例如addUser()

4. advice： 通知/增强，增强代码。例如after，before

5. Weaving ： 织入，是指把增强advice应用到目标对象target来创建的代理对象proxy的过程。

6. proxy 代理类

7. Aspect 切面 是把pointcut和通知advice的结合。

   ​	一个是一个特殊的面

   ​	一个切入点和一个通知，组合成一个特殊的面

![](C:\Users\asus\Desktop\aspect.png)


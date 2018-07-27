> 从Java EE 5规范开始，Servlet中增加了两个影响Servlet生命周期的注解（Annotion）；@PostConstruct和@PreDestroy。这两个注解被用来修饰一个非静态的void()方法 。写法有如下两种方式：

```java
@PostConstruct
Public void someMethod() {}
```

或者

```java
public @PostConstruct void someMethod(){}
```

> 被@PostConstruct修饰的方法会在服务器加载Servle的时候运行，并且只会被服务器执行一次。PostConstruct在构造函数之后执行,init()方法之前执行。PreDestroy（）方法在destroy()方法执行执行之后执行


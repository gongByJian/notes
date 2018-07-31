```
InitializingBean, DisposableBean,, ApplicationListener, BeanNameAware 

 NamespaceHandlerSupport

 BeanDefinitionParser
```

##### PropertyPlaceholderConfigurer

```
Property扩展  需extends PropertyPlaceholderConfigurer
```

```xml
<bean id="propertyConfigurer"class="org.springframework.beans.factory.config.PropertyPlaceholderConfigurer">
   <property name="locations">
     <value>conf/jdbc.properties</value>
   </property>
    <property name="fileEncoding">
      <value>UTF-8</value>
    </property>
</bean>

<bean id="propertyConfigurer"class="org.springframework.beans.factory.config.PropertyPlaceholderConfigurer">
   <property name="locations">
            <list>
                <value>classpath:/META-INF/app.properties</value>
            </list>
    </property>
    <property name="fileEncoding">
      <value>UTF-8</value>
    </property>
</bean>

```

##### ApplicationContextAware

```
Spring容器会检测容器中的所有Bean，如果发现某个Bean实现了ApplicationContextAware接口，Spring容器会在创建该Bean之后，自动调用该Bean的setApplicationContextAware()方法，调用该方法时，会将容器本身作为参数传给该方法——该方法中的实现部分将Spring传入的参数（容器本身）赋给该类对象的applicationContext实例变量，因此接下来可以通过该applicationContext实例变量来访问容器本身。
```

##### ImportBeanDefinitionRegistrar  since 3.1 注册bean

spring在处理@Configuration的时候会去调用第三方的实现类registerBeanDefinitions注册类

```
registerBeanDefinitions
```

##### ClassPathBeanDefinitionScanner

##### 工具类:

```
ClassUtils
StringUtils
```




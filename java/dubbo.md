## DOBBO

#### 官网 http://dubbo.apache.org

dubbo

- ##### 多版本支持

  - ```
    <dubbo:service interface="com.zhuyizhuo.java.IHelloService"  ref="helloService" protocol="dubbo" version="1.0.0" />
    ```

- ##### 多协议支持

  - ```
    protocol为协议  单个接口多协议 或者多个接口多协议都支持  单接口多协议时需单独声明协议如下
       <dubbo:protocol port="20880" name="dubbo"/>
       <dubbo:protocol port="80" name="hessian"/>
    <dubbo:service interface="com.zhuyizhuo.java.IHelloService"               ref="helloService" protocol="dubbo,hessian" />
    ```

  - ###### 默认端口号:

    ```
    dubbo ： 20880
    rmi : 1099
    http : 80
    hessian : 80
    webservice : 80
    ```

- ##### 多注册中心支持

- ##### 启动检查机制

- ##### 主机绑定

  - ###### 主机绑定源码解析

    - ```
      dubbo-config
      	dubbo-config-api
              ServiceConfig
                  doExportUrlsFor1Protocol() 获取一个host地址
      ```

- ##### 集群容错

- ##### 服务降级

##### 

##### dubbo的SPI

1. 需要在resource目录下配置META-INF/dubbo或者META-INF/dubbo/internal或者META-INF/services，并基于SPI接口去创建一个文件

2. 文件名称和接口名称保持一致，文件内容和SPI有差异，内容是KEY对应Value：

   ```
   myProtocal=com.zhuyizhuo.java.protocal.DefineProtocal
   ```

##### 源码分析切入点

```
ExtensionLoader.getExtensionLoader(Protocol.class).getAdaptiveExtension();
```

缓存 file 制定缓存路径及文件名
```
<dubbo:registry address="zookeeper://zookeeper.com:2181" file="d:/dubbo-service"/>
```



ExtensionLoader
  301 
  getExtension
    createExtension
      getExtensionClasses
        loadExtensionClasses


  
  getAdaptiveExtension
    createAdaptiveExtension
      getAdaptiveExtensionClass
        getExtensionClasses
          loadExtensionClasses
        createAdaptiveExtensionClass
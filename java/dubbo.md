## DOBBO

#### 官网 http://dubbo.apache.org

##### 源码解析

```
dubbo-config
	dubbo-config-api
        ServiceConfig
            doExportUrlsFor1Protocol() 获取一个host地址
            默认端口号:
                dubbo ： 20880
                rmi : 1099
                http : 80
                hessian : 80
                webservice : 80
```

##### 切入点

```
ExtensionLoader.getExtensionLoader(Protocol.class).getAdaptiveExtension();
```

dubbo 47:31
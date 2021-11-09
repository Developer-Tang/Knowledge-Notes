##  Spring核心组件

![Spring核心组件](Spring基础知识/Spring核心组件.drawio.svg)



## SpringIOC原理

### IOC简介

> Spring通过一个配置文件描述Bean及Bean之间的依赖关系，利用 Java 语言的反射功能实例化Bean并建立Bean之间的依赖关系。 Spring的IOC容器在完成这些底层工作的基础上，还提供了Bean实例缓存、生命周期管理、 Bean实例代理、事件发布、资源装载等高级服务。

### Spring 容器高层视图

> Spring启动时读取应用程序提供的Bean配置信息，并在Spring 容器中生成一份相应的Bean配置注册表，然后根据这张注册表实例化Bean，装配好Bean之间的依赖关系，为上层应用提供准备就绪的运行环境。其中Bean缓存池为HashMap实现

![SpringBean调用简图](Spring基础知识/SpringBean调用简图.drawio.svg)


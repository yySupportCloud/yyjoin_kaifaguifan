# 日志依赖引入

平台统一使用依赖iuap-log组件方式对日志的接口和实现进行引入，iuap-log组件间接依赖slf4j和logback相关jar包，同时依赖了对各种其他日志组件的适配桥接包。引入方式如下：

![](images/kaifaguifan-6.png)

iuap-log组件默认引入slf4j、logback和各种桥接包对应的依赖，依赖关系如下：

![](images/kaifaguifan-7.png)


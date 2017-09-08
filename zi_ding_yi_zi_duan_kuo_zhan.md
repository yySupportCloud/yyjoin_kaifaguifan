# 自定义字段扩展

Logback支持自定义日志输出格式，可以根据业务需求增加整体日志输出的内容。业务可以在调用的开始阶段，通过filter的方式加入到logback的线程绑定变量中，后续的日志输出都会携带相关内容。

在logback.xml中定义pattern时，定义自定义属性如[%X{key_example}]，其中key_example为自定义的属性名，在filter中设置内容，如当前登录用户、整体事务ID、日志的全局追踪ID等，可以在所有的后续日志输出时统一打印，方便后续的日志收集和调用跟踪，问题排查。平台规范输出如下：

![](kaifaguifan-9.png)

Filter中可以初始化自定义属性的值，org.slf4j.MDC类会将值放置在当前线程的线程绑定变量中，示例如下：

![](kaifaguifan-10.png)
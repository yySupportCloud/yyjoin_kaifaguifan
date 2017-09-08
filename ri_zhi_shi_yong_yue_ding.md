# 日志使用约定

1：强制要求  
应用中不可直接使用日志系统（Log4j、Logback）中的API，而应依赖使用日志框架
SLF4J中的API，使用门面模式的日志框架，有利于维护和各个类的日志处理方式统一。  

2：强制要求  
对trace/debug/info级别的日志输出，必须使用条件输出形式或者使用占位符的方
式。 说明：logger.debug("Processing trade with id: " + id + " symbol: " + symbol); 
如果日志级别是warn，上述日志不会打印，但是会执行字符串拼接操作，如果 symbol是对象，会执行toString()方法，浪费了系统资源，执行了上述操作，最终日志却没有打印。
正确示例：

    if (logger.isDebugEnabled()) {    
    logger.debug("Processing trade with id: " + id + " symbol: " + symbol);  
    }       

    logger.debug("Processing trade with id: {} symbol : {} ", id, symbol);  

3：强制要求  
异常信息应该包括两类信息：当前异常信息和异常堆栈信息。如果不处理，那么往上
抛。示例如下：

    logger.error(各类参数或者对象 toString + "_" + e.getMessage(), e);
    
4：强制要求  
谨慎地记录日志。生产环境禁止输出 debug日志；有选择地输出 info日志；如果使
用warn来记录刚上线时的业务行为信息，一定要注意日志输出量的问题，避免把服务器磁盘撑爆，并记得及时删除这些观察日志。 大量地输出无效日志，不利于系统性能提升，也不利于快速定位错误点。

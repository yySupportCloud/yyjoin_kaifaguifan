# 日志打印

1：logger声明  

    import org.slf4j.Logger;         
    import org.slf4j.LoggerFactory; 
    private static final Logger logger = LoggerFactory.getLogger(Abc.class); 
    
2：日志打印  
错误日志：logger.error("this is a {} demo! ", "exception log", e);  
INFO日志：logger.info("this is a {} log demo! level is：{}", "multi params", "info");

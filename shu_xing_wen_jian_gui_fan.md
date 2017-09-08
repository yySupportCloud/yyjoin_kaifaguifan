# 属性文件规范

1：属性文件格式为UTF-8，名称统一为application.properties；  
2：iuap-utils提供组件和工具类PropertyUtils，读取属性配置；  
3：属性文件的加载方式为PropertyPlaceholderConfigurer，读取按照配置规定顺序；

![](kaifaguifan-2.png)

此配置放置于spring的主配置文件中。系统属性 > 环境变量 > 属性文件。  
4：如果使用配置中心，按照配置中心的配置规范。

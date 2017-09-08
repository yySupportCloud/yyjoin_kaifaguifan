# 类、变量、常量规范

1：强制约定  
类名使用UpperCamelCase风格，必须遵从驼峰形式，但以下情形例外：DO / BO / 
DTO / VO / AO。  
正例：MarcoPolo / UserDO / XmlService / TcpUdpDeal / TaPromotion   
反例：macroPolo / UserDo / XMLService / TCPUDPDeal / TAPromotion

2：强制约定  
方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase风格，必须遵从
驼峰形式。  
正例： localValue / getHttpMessage() / inputUserId

3：强制约定  
常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚。  
正例： MAX_STOCK_COUNT   
反例： MAX_COUNT

4：强制约定  
抽象类命名使用Abstract或Base开头；异常类命名使用 Exception结尾；测试类
命名以它要测试的类的名称开始，以 Test结尾。

5：强制约定
POJO类中布尔类型的变量，都不要加 is，否则部分框架解析会引起序列化错误。   
反例：定义为基本数据类型 Boolean isDeleted；的属性，它的方法也是 isDeleted()，RPC  
框架在反向解析的时候，“以为”对应的属性名称是 deleted，导致属性获取不到，进而抛出异常。

6：建议

如果使用到了设计模式，建议在类名中体现出具体模式。：将设计模式体现在名字中，有利于阅读者快速理解架构设计思想。正例如下：  
public class OrderFactory;   
public class LoginProxy;   
public class ResourceObserver;

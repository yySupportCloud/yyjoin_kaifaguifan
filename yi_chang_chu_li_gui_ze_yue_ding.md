# 异常处理规则约定

**1：强制要求：**  
Java 类库中定义的一类 RuntimeException可以通过预先检查进行规避，而不应该
通过catch 来处理，比如：IndexOutOfBoundsException，NullPointerException等等。 
说明：无法通过预检查的异常除外，如在解析一个外部传来的字符串形式数字时，通过 catch 
NumberFormatException来实现。 

**2：强制要求**  
    避免对大段代码进行 try-catch，catch时请分清稳定代码和非稳定代码，稳定代码指的是无论如何不会出错的代码。对于非稳定代码的 catch尽可能进行区分异常类型，再做对应的异常处理。  
    
**3：强制要求**  
    有try块放到了事务代码中，catch异常后，如果需要回滚事务，一定要注意手动回
滚事务或者抛出可令事务回滚的异常。 

**4：强制要求**  
finally块必须对资源对象、流对象进行关闭，有异常也要做 try-catch。 如果JDK7及以上，可以使用try-with-resources方式。

**5：强制要求**  
    禁止在finally块中使用return语句，finally块中的return返回后方法结束执行，不会再执行try块中的 return语句。
    
**6：建议**  
方法的返回值可以为 null，不强制返回空集合，或者空对象等，必须添加注释充分
说明什么情况下会返回 null值。调用方需要进行 null判断防止NPE问题。即使被调用方法返回空集合或者空对象，对调用者来说，也必须考虑到远程调用失败、序列化失败、运行时异常等场景返回null的情况。容易产生NPE的操作如下：  
1）返回类型为基本数据类型，return 包装数据类型的对象时，自动拆箱有可能产生NPE。                                                                            
2）数据库的查询结果可能为 null。   
3）集合里的元素即使 isNotEmpty，取出的数据元素也可能为 null。   
4）远程调用返回对象时，一律要求进行空指针判断，防止NPE。   
5）对于Session中获取的数据，建议NPE检查，避免空指针。   
6）级联调用obj.getA().getB().getC()；一连串调用，易产生 NPE。  

**7：建议**  
定义时区分 unchecked  /  checked 异常，避免直接抛出new  RuntimeException()，
更不允许抛出Exception或者Throwable，应使用有业务含义的自定义异常。推荐业界已定义过的自定义异常，如：DAOException / ServiceException等。

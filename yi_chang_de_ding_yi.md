# 异常的定义

Java定义了一个异常类的层次结构,其以Throwable开始，扩展出Error和Exception，而Exception又扩展出RuntimeException. 这四个类是泛化的，并不提供多少出错信息，除了Java提供了大量异常子类，平台也提供了如 SysPromptException，ValidateException，WebRuntimeException等异常类型。如需更加具体，可以定义自己的异常类。 在定义和使用异常的时候要遵循以下几个原则：
*	不要将异常用于控制流,仅为异常情况使用异常；
*	对可恢复异常情况使用检查型异常；对编程错误如前置条件错误等情况使用运行时异常；
*	避免使用不必要的检查型异常,不要对调用者根本就不可能恢复的情况或者说可以预见到必然会使程序退出的情况使用检查型异常；
*	抛出异常应与抽象层次相适应，方法抛出的异常必须和该方法所实现的功能在抽象层次上一致。
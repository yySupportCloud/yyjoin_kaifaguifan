# 异常的捕获和抛出

Java语言规范中给出了三个抛出异常的原因：  
（1）Java虚拟机同步（synchronized）检测到反常的（abnormal）执行条件，这些条件可能由下列条件触发：
*	对表达式的求值违反了语言的语义，例如除0等
*	加载或链接程序某部分的时候发生了错误
*	超出了某些资源的限制，比如内存不足等  

（2）throw语句被执行  
（3）发生了异步异常
*	Thread或ThreadGroup的stop方法被调用
*	虚拟机发生了内部错误 Java语言规范也明确指出了异常的三种类型：RuntimeException、Error和checkedException（检查型异常）。第一种类型的异常称为非检查型异常（uncheckedException），不需要声明，所以不需要程序员显式地使用try...catch语句来捕获它们；而后面两种则要求声明，即必须使用try...catch来捕获并处理。  
通过提早抛出异常（又称＂迅速失败＂），异常得以清晰又准确。堆栈信息立即反映出错的原因和位置，其中包含的异常信息应提供更加丰富的信息用来定位问题。迅速失败可以有效避免不必要的对象构造或资源占用。  
捕获异常与抛异常，必须是完全匹配，或者捕获异常是抛异常的父类。  
Java可以对同一try块定义多个catch块，从而对每种异常分别进行恰当的处理。  
捕获异常时尽量明确异常的类型，对于当前程序没有能力处理这个异常的时候不要处理，应该在方法的throws子句声明异常，把异常处理的责任往调用链的上游传递。 过早捕获异常，通常会导致更严重的错误和其他异常。不要不分类型就立即将代码用try块包装起来并使用catch捕获异常。  
建议不使用异常捕获的方式做流程控制或者条件控制，异常处理效率低。  
异常的捕获是为了更好的处理，尽量避免捕获异常后不做任何处理，直接抛出，如果不处理，则声明方法时直接抛出给调用者。最外层的使用者，必须捕获处理异常，并处理为可以识别的易于理解的内容。

# AOP模块使用方式
AOP模块可以截获类的实例中的方法的上下文, 帮助探测方法性能, 方法调用拦截过滤以及进行其他自定义扩展. 目前架构中已经集成了AOP方法日志.
1. 对待拦截的类和方法添加AOP特性, 并继承ContextBoundObject,例如:
```C#
[AOP]
public class AopTest : ContextBoundObject
{
     [AOPMethod(typeof(AOPLogHandler))]
     public void DO(string id, int a, decimal b, List<string> list)
     { 
      
     }
}
```
其中AOPLogHandler是实现IAOPHandler接口的处理拦截事件的具体实现.
2. 正常调用方法, 日志会记录到本地文件里.
3. 开关AOP日志可以在[log4net.config](../configintro/log4netpei_log4net_config.md)中配置


# 3.7 日志模块使用方式
日志模块基于log4net进行扩展, 支持自定义参数, 从而更好的依照业务需求进行日志记录. 架构中集成了通用日志记录方法, 监控日志记录方法以及网站和服务的日志记录方法.
1. 通用日志,在非站点和wcf服务中使用
```C#
public class CommonLogger : Logger
{
  public static void LogError(object message, Exception ex); 
  public static void LogInfo(object message);
}
```
2. Web日志（站点中使用）:
```C#
public class WebLogger : Logger
{
  public static void LogError(object message, Exception ex);
  public static void LogInfo(object message);
}
```
与CommonLogger的区别在于WebLogger可以自动记录访问者IP, 请求的Url, 所在服务器等, 推荐在站点中使用.

3. Service日志（服务中使用）：
```C#
public class ServiceLogger : Logger
{
  public static void LogError(object message, Exception ex);
  public static void LogInfo(object message);
}
```
与CommonLogger的区别在于ServiceLogger可以自动记录服务名称, 所在服务器等, 推荐在服务中使用.

4. 将log4net.config文件置于MonitorFiles/Config下. 具体配置log4net.config, 请参照[配置示例][www.baidu.com].


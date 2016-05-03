# 异常调式配置(ExceptionConfig)

异常显示控制开关,只针对继承UtourControllerJson的Controller起作用.
  
配置结构及样例：
```xml
<?xml version="1.0" encoding="utf-8"?>
<!--fasle：当返回Json数据结果的Action出现异常时，不返回具体错误异常，true：返回具体的错误异常信息
，以便开发调试-->
<ExceptionConfig>
  <DebugMode>false</DebugMode>
</ExceptionConfig>
````


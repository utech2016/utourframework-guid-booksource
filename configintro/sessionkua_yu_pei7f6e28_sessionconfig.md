# Session共享配置(SessionConfig)

配置会话Cookie存储的域名，使用Session共享时则需要将多个站点统一个相同域名。

配置结构及样例
```xml
<?xml version="1.0" encoding="utf-8" ?>
<SessionConfig>
  <!--SessionDomain 配置会话Cookie存储的域名，使用Session共享时则需要将多个站点统一个相同域名配置-->
  <SessionDomain>demo.com</SessionDomain>
</SessionConfig>
```
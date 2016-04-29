# 4 框架配置说明
框架配置，提供了基于框架开发所需的各种类型的配置，使用框架的配置后，项目对web.config的依赖作用削弱至最低, 仅仅配置最基本的节点（见下方）, 将其他配置按类别集中归置到特定区域, 并进行实时监控, 实现了动态配置, 大大方便和简化了配置过程.

####框架配置要求

* 需要在每个启动项目的配置文件web.config或app.config中设置配置文件的监控目录
  ```xml
  <appSettings>
    <!--配置监控目录，目录可自定义，但必须是从项目根目录开始的相对地址-->
    <add key="MonitorFilesPath" value="MonitorFiles" />
  </appSettings>
  ```
* 必须把配置文件要统一放到 “监控目录/Config”下，sqlmap配置放到“监控目录/SqlMap”下





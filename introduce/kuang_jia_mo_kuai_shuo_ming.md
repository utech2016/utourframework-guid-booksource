# 1.1.框架模块说明
* **Utour.Framework.Core**
  >核心库,AOP实现，服务连接池管理，Emit动态编译（客户端服务代理编译）
* **Utour.Framework.Context**
  >自定义上下文:服务上下文，网站上下文,存储网站服务会话的每次交互调用的相关参数信息
* **Utour.Framework.Service**
  >完成服务宿主和服务行为配置，创建和发布，WCF服务动态代理生成，并为客户端提供了统一调用WCF服务的方式
* **Utour.Framework.Web**
  >统一Session存储，通过简单配置实现不同站点的Session共享，统一Controller拦截错误处理，统一Json结果处理返回,WebApi调用封装，WebApi接口缓存
* **Utour.Framework.Config**
  >配置统一管理监控实时更新，提供客户自定义配置，可通过配置工厂读取自定义配置，目前框架已提供了内置的几种配置，详细见[框架内置配置说明][0]
* **Utour.Framework.Cache**
  >提供不同缓存(目前框架已提供Redis,Memcached，AppFabric,IIS Cache)的基础操作API,内置缓存适配器接口，提供开发人员继承实现不同业务类型的缓存操作适配器，并可通过框架缓存配置和缓存适配器工厂完成动态注入和调用
* **Utour.Framework.DataBase**
  >提供不同类型数据库(目前框架只提供了SQLServer和MongoDB)的操作帮助类,内置数据适配器接口，提供开发人员继承实现不同业务类型的数据操作适配器，并可通过框架数据库配置和数据库适配器工厂完成动态注入和调用
* **Utour.Framework.Utility**
  >框架封装的各种工具类,如JSON格式化，序列化，加密等
* **Utour.Framework.Log**
  >基于log4net扩展实现的框架的自定义类型日志，提供了CommonLogger,WebLogger,ServiceLogger三种不同场景下(站点项目,WCF服务项目,其他类型项目)的Logger日志记录类
* **Utour.Framework.CAInterface**
  >提供基本缓存操作接口层，如提供通用缓存接口操作等
* **Utour.Framework.CacheAccess**
  >对Utour.Framework.CAInterface接口层的缓存实现






[0]:http://www.baidu.com/

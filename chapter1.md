# 1.框架概括

**1.0框架整体包含11个项目，即11个dll(未来可能根据版本会有所增加)，如图所示：**
![框架项目结构](img1.png)

## 1.1 框架模块说明
* **Utour.Framework.Core**
  >核心库,AOP实现，服务连接池管理，Emit动态编译
* **Utour.Framework.Context**
  >自定义上下文。服务上下文，网站上下文,存储网站服务会话的每次交互调用的相关参数信息
* **Utour.Framework.Service**
  >服务宿主创建发布，服务动态代理生成，客户端统一调用，服务器行为扩展
* **Utour.Framework.Web**
  >统一Session存储，统一Controller拦截错误处理，统一Json结果处理返回,WebApi调用封装，WebApi接口缓存
* **Utour.Framework.Config**
  >配置统一监控实时更新，提供客户自定义配置，可通过配置工厂读取自定义配置
* **Utour.Framework.Cache**
  >













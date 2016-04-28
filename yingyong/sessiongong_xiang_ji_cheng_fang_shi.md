# 3.5 Session共享集成方式
架构中为了使Session可以跨域使用, 使用Redis作为Session的存储介质.
1. 引用程序集
  >Utour.Framework.Web.dll
  >Utour.Framework.Session.dll
2. 使Global.asax.cs的```MvcApplication```类继承```Utour.Framework.Web.MvcApplicationBase```.
3. 重写Application_Start(), 方法最后调用```base.Application_Start()```以完成Session存储Redis准备工作
```C#
protected override void Application_Start()
{
		//这儿写应用程序启动时的逻辑
		//TODO:......
		base.Application_Start();
}
```
4. 在Session.Config中配置站点的Domain,如下
```xml
<SessionConfig>
  <SessionDomain>uzai.com</SessionDomain>
</SessionConfig>
```
5.在CacheProvider.Config中配置Redis连接串
```xml
<CacheProvider category="Redis">
      <CacheConnections>
       <CacheConnection name="SessionCache" readConnectionsString="127.0.0.1:6379"  writeConnectionsString="127.0.0.1:6379" maxWirtePoolSize="100" maxReadPoolSize="100" regionName="0"/>
      </CacheConnections>
</CacheProvider>
```
6.在Web.config中配置节点
```xml
<system.web>
    <sessionState mode="Custom" customProvider="RedisSessionStateProvider">
      <providers>
        <clear />
        <add name="RedisSessionStateProvider"
             type="Harbour.RedisSessionStateStore.RedisSessionStateStoreProvider"/>
      </providers>
    </sessionState>
    <httpModules>
  <!--IIS经典模式下，在此配置Session跨域模块-->
  <add   name="SessionCookieDomainHttpModule" type="Utour.Framework.Web.SessionCookieDomainHttpModule,Utour.Framework.Web"/>
    </httpModules>
</system.web>
<system.webServer>
    <modules>
<!--IIS集成模式下，在此配置Session跨域模块-->      
<add name="SessionCookieDomainHttpModule" type="Utour.Framework.Web.SessionCookieDomainHttpModule,Utour.Framework.Web"/>
    </modules>
</system.webServer>
```
7.**注意: 由于Session的存储介质不再是内存, 请确保待存储的对象可序列化(Serializable).
即要在实体类上面打上Serializable标记属性**


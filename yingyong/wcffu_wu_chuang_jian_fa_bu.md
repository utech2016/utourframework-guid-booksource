# 3.2 WCF服务创建发布
 
 架构中不再使用传统wcf创建和发布的方式，使用.net4.0 wcf中新特性实现了无.svc服务的发布方式，框架还支持的多种wcf服务绑定协议和不同宿主的发布。
 
 ####wcf服务创建(BasicHttpBinding)
 
 1. 新建服务实体类User
 2. 在服务接口层(Utour.DemoDataService.ServiceInterface)创建一个业务单元服务接口即契约(Contract)，如：IUserService,使其继承Utour.Framework.Service.IService接口，并使用[ServiceContract]标记该接口
 3. 添加接口方法列表，每个方法加上[OperationContract]标记
 4. 在业务层（Utour.DemoDataService.Business）新建一个对上步接口的实现类，如UserService，并实现IUserService接口

###wcf服务发布(BasicHttpBinding)

1.在启动项目的Web.config文件serviceActivations节点中加入服务自动激活配置
  ```xml
    <system.serviceModel>
    <serviceHostingEnvironment  multipleSiteBindingsEnabled="true" aspNetCompatibilityEnabled="false">
      <serviceActivations>
        <add service="Utour.DemoDataService.Business.UserService" 
             relativeAddress="UserService.svc" 
             actory="Utour.Framework.Service.WCFServiceHostFactory"
         />
        </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
  ```
2. 在```ServiceHost.config```文件的WCFServiceHosts节点加入一个WCFServiceHost服务宿主配置（[详细配置说明](../configintro/fu_wu_su_zhu_pei_7f6e28_servicehostconfig.md)）
```xml
     <WCFServiceHost serviceName="Utour.DemoDataService.Business.UserService" baseAddress ="">
      <Endpoints>
        <ServiceEndpoint category="WCFClassic" 
                          relativeAddress="" 
                          contract="Utour.DemoDataService.ServiceInterface.IUserService" />
      </Endpoints>
    </WCFServiceHost>
```
## WCF服务创建发布
 
 架构中不再使用传统wcf创建和发布的方式，使用.net4.0 wcf中新特性实现了无.svc服务的发布方式，框架还支持的多种wcf服务绑定协议和不同宿主的发布。
 
 ###wcf服务创建(BasicHttpBinding)
 
 1. 新建服务实体类User
 
 2. 在服务接口层(Utour.DemoDataService.ServiceInterface)创建一个业务单元服务接口即契约(Contract)，如：IUserService,使其继承Utour.Framework.Service.IService接口，并使用[ServiceContract]标记该接口
 
 3. 添加接口方法列表，每个方法加上[OperationContract]标记

 4. 在业务层（Utour.DemoDataService.Business）新建一个对服务接口的实现类，如UserService，并实现IUserService接口

    示例代码
    ```C#
    /// <summary>
    /// 用户数据服务接口
    /// </summary>
    [ServiceContract]
    public interface IUserService : Utour.Framework.Service.IService
    {

        [OperationContract]
        bool AddUser(User user);

        [OperationContract]
        User LoadUser(int Id);

        [OperationContract]
        bool DeleteUser(int Id);

        [OperationContract]
        List<User> GetUserList();
    }
   ```
   
###wcf服务发布(BasicHttpBinding)

1. 在宿主项目```Web.config```文件的```serviceActivations```节点中加入服务自动激活配置

  框架Demo中的示例
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
  
2. 在```ServiceHost.config```文件的```WCFServiceHosts```节点加入一个```WCFServiceHost```服务宿主配置（[详细配置说明](../configintro/fu_wu_su_zhu_pei_7f6e28_servicehostconfig.md)）

   框架Demo中的示例
  ```xml
     <WCFServiceHost serviceName="Utour.DemoDataService.Business.UserService" baseAddress ="">
      <Endpoints>
        <ServiceEndpoint category="WCFClassic" 
                          relativeAddress="" 
                          contract="Utour.DemoDataService.ServiceInterface.IUserService" />
      </Endpoints>
    </WCFServiceHost>
  ```
  
3. 启动宿主项目，发布wcf服务
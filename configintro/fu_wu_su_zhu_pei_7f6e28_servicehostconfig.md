# 服务宿主配置(ServiceHostConfig)
wcf 服务宿主配置，对应配置文件ServiceHost.config,此配置完全将传统创建wcf服务自动生成的一堆配置进行化繁为简，使其配置更加清晰明了，避免了因服务过多而导致web.config的庞大臃肿。

配置结构及样例:
```xml
<?xml version="1.0" encoding="utf-8"?>
<!--wcf服务宿主配置，支持多宿主(Host)，多终结点(EndPoint)，多绑定(Binding)配置-->
<ServiceHostConfig>
  <!--服务宿主集合，每发布一个wcf服务都需要在此节点添加一个WCFServiceHost配置-->
  <WCFServiceHosts>
    <!--wcf服务寄宿宿主配置，节点配置属性说明
       serviceName：服务接口实现类全名称
       baseAddress：服务的基地址(当category为MSMQ，TCP时属性为必须设置项，其他情况默认可设为"")
    -->
    <WCFServiceHost serviceName="Utour.DemoDataService.Business.UserService" baseAddress ="">
      <Endpoints>
        <!--
        服务终结点配置，节点配置属性说明
        category：服务绑定(Biding)类型，可配置的属性值即含义如下（必须）
                  WCFClassic—经典WCF模式，对应 BasicHttpBinding
                  RESTful—Rest协议风格WCF，对应WebHttpBinding
                  WSHttp—Web Service，对应WSHttpBinding，可将ASP.NET项目应用作为宿主发布服务
                  MSMQ—支持基于MSMQ队列宿主，对应NetMsmqBinding
                  TCP-基于TCP协议服务发布，对应NetTcpBinding
        relativeAddress：服务的相对地址(当category 为MSMQ，TCP时，此属性为必须设置项，其他默认设为""即可)
        contract：服务端契约，即服务端接口全限定名称（必须）
        -->
        <ServiceEndpoint category="WCFClassic" relativeAddress="" contract="Utour.DemoDataService.ServiceInterface.IUserService" />
      </Endpoints>
    </WCFServiceHost>
  </WCFServiceHosts>
</ServiceHostConfig>
```
# 服务客户端配置(ServiceClientConfig)
ServiceClientConfig wcf服务客户端引用配置，对应配置文件ServiceClient.config.

配置结构及样例:
```xml
<?xml version="1.0" encoding="utf-8"?>
<!--WCF客户端引用服务配置文件，每引用一个外部WCF接口服务时，则需要在Client节点添加一行ClientEndpoint客户端配置-->
<ServiceClientConfig>
  <Client>
    <!--                        
    该节点可配置的属性列举如下：
    address：表示外部wcf服务接口的可调用地址 （必须）
    binding：配置以什么方式协议与服务端进行通讯，按照服务宿主的协议发布方式，有以下几种配置（必须）
              1)basicHttpBinding 2)wsHttpBinding 3)netTcpBinding 4)netMsmqBinding 5)webHttpBinding
    contract：服务端接口契约，此处即配置服务端接口全名称（必须）
    maxReceivedMessageSize：消息最大接受大小（默认值：6553600）(可选)
    maxStringContentLength：最大可接受字符内容长度（默认值：819200）(可选)
    reliableSessionEnabled：是否启用可靠的会话，在使用TCP通讯协议时，配置才生效(可选)
    openTimeout：打开wcf连接通道超时时间,格式 hh:mm:ss（默认值：00:00:05）(可选)
    closeTimeout:关闭wcf连接通道超时时间，格式 hh:mm:ss（默认值：00:00:05）(可选)
    sendTimeout：发送数据超时时间，格式 hh:mm:ss（默认值：00:00:05）(可选)
    receiveTimeout：接受数据超时时间，格式 hh:mm:ss（默认值：00:00:05）(可选)
    -->
    <ClientEndpoint address="" binding="basicHttpBinding"
                    contract=""
                    maxReceivedMessageSize="65536000" maxStringContentLength="8192000"
                    sendTimeout="00:02:00" receiveTimeout="00:02:00"/>
  </Client>
</ServiceClientConfig>
```

# 缓存提供者配置(CacheProviderConfig)

CacheProviderConfig缓存提供者配置类，对应配置文件```CacheProvider.config```,项目所需的所有缓存连接串在此配置文件中配置.

### 配置结构及样例
```xml
<?xml version="1.0" encoding="utf-8"?>
<!--缓存连接配置，同一种category只能对应一个CacheProvider配置，不得重复出现，缓存连接串请在对应CacheConnections节点下添加-->
<CacheProviderConfig>
  <CacheProviders>
    <!--缓存提供配置，category缓存类别，可选类别有
        Redis:Redis缓存
        AppFabric:AppFabric缓存
        Memcached:Memcached缓存
        Local：使用本地缓存，即使用内置的System.Web.Caching.Cache类
    -->
    <CacheProvider category="Redis">
      <CacheConnections>
      <!--
       缓存连接串，可按照功能模块进行缓存连接串配置，可配置属性：
       name：缓存连接名称，建议按照功能模块划分（必须）
       readConnectionsString：只读缓存连接串,集群模式，以','分隔（必须）
       writeConnectionsString：可写缓存连接串，集群模式，以','分隔（必须）
       maxWritePoolSize：“写”链接池链接数（默认为10）目前针对Redis缓存生效(可选)
       maxReadPoolSize：“读”链接池链接数 (默认为10)，目前针对Redis缓存生效(可选)
       regionName：缓存范围名称，当缓存为Redis时，regionName即redis的db名称，因redis中的db默认以整数数字命名，因此必须为redis可支持最大db之间的数字(必须),针对       
      -->
        <CacheConnection name="BusinessCache" readConnectionsString="127.0.0.1:6379" writeConnectionsString="127.0.0.1:6379" regionName="1"/>
      </CacheConnections>
    </CacheProvider>
  </CacheProviders>
</CacheProviderConfig>
```
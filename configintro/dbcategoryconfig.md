# 缓存适配器配置(CacheCategoryConfig)
缓存适配器类配置，对应配置文件CacheCategory.config在此配置项目中所有实现业务缓存适配器接口的适配器类，在用```CacheAdapterFactory```获取对应适配器接口实例时，框架会根据此配置动态注入生成对应适配器实例。

配置结构及样例：
```xml
<?xml version="1.0" encoding="utf-8"?>
<!--缓存适配器配置，每一个缓存适配器都需要在此进行配置-->
<CacheCategoryConfig>
<!--
 缓存适配器,在这里配置已经实现某一业务缓存接口的适配器实例
 name：业务单元名称，如业务适配器类名称为DictCacheAdaperForRedis（业务单元名称 + CacheAdapter + 
       For缓存类别）则name应配置为Dict
cacheCategory:缓存类别，可选缓存类别如下
                  Redis:Redis缓存
                  AppFabric:AppFabric缓存
                  Memcached:Memcached缓存
                  Local：使用本地缓存，即使用内置的System.Web.Caching.Cache类
 -->
  <CacheAdapters>
    <CacheAdapter name="Dict" cacheCategory="Redis"/>
  </CacheAdapters>
</CacheCategoryConfig>
```

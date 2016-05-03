# WebApi接口缓存配置(WebApiCacheConfig)

WebApi接口缓存配置,可配置对某一个Controller的某个方法的返回结果进行缓存。

###配置结构及样例

```xml
<?xml version="1.0" encoding="utf-8"?>
<WebApiCacheConfig>
  <ApiCacheSettingList>
    <!--
      一个接口对应一个ApiCacheSetting节点，节点属性说明
      apiName：接口名称（自定义）
      controller：接口对应controller的名称
      action：接口对应action的名称
      expireTime：接口数据缓存相对时间，单位:分钟
      isCache：缓存开关，是否进行缓存
    -->
    <ApiCacheSetting apiName="getusers" controller="Users" 
                      action="GetUserList" expireTime="10"  
                      isCache="true" />
  </ApiCacheSettingList>
</WebApiCacheConfig>
```
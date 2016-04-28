# 3.8 WebAPI调用集成
对WebApi调用和格式在框架中进行了统一封装，并提供了api接口数据缓存功能，具体使用请按照如下方式：
1. 直接依赖dll引入
- tour.Framework.Web.dll
- Utour.Framework.CacheAccess.dll
- Utour.Framework.CAInterface.dll
2. 加入两项配置文件
   WebApiAuth.config--api如有授权验证，则在调用方需加入此配置
   WebApiCache.config--在api服务层配置哪些接口需要进行结果缓存
3. 在api项目WebApiConfig类Register方法加入下面三行代码配置
```C#
  //注册全局接口缓存Filter，统一接口Json结果格式
  config.Filters.Add(new WebApiDataCacheFilterAttribute("damoapi.utour.com"));
  //注册全局接口异常Filter
  config.Filters.Add(new WebApiExceptionFilter());
  //清除默认xml接口默认格式，启用Json格式
  config.Formatters.Remove(config.Formatters.XmlFormatter);
 ```
4. 因框架已统一Json结果格式，编写每个web api 返回值只需要纯粹返回业务实数据对象即即可，无需再Json序列化结果，框架内部会自动序列化结果并根据配置写入缓存，如图

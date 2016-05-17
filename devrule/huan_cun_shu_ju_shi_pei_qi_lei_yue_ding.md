## 缓存数据适配器类约定
数据适配器类定义在```Utour.DemoDataService.CacheAccess```工程内; 数据适配器类是对数据访问接口约定的方法的具体实现, 对缓存的访问操作封装在数据适配器代码内.
>1. 数据访问实现类，需要从```CacheAdapterBase```基类, ```Framework.Cache.ICacheAdapter```和对应的数据访问接口继承.
>2. 同一数据访问接口对应的多个数据适配器, 一般为对同一数据访问接口在不同种缓存上的实现.
例如: ```UserCacheAdaperForRedis```和```UserCacheAdaperForMemcached```分别对应```IUserCacheAdapter```接口在Redis和Memcached缓存上的实现
>3. 数据适配器类名称格式为: ```业务单元名称 + CacheAdapter + For缓存类型```


# 3.4 缓存访问层调用方式
架构中的缓存访问都是按照业务划分在不同的Adapter中, 调用时是根据接口动态生成相应的Adapter实例.
>1. 引用数据访问接口CAInterface项目和业务实体(Entity)项目.
>2. 在[CacheCategory.config](../configintro/dbcategoryconfig.md)文件中配置对应业务缓存适配器
>3. 在业务逻辑层使用```Utour.Framework.Cache.CacheAdapterFactory.GetCacheAdapter<T>()```方法进行调用

  ```C#
  IUserCacheAdapter userCA=CacheAdapterFactory.GetInstance().GetCacheAdapter<IUserCacheAdapter>();
  List<User> userList = userCA.GetList();
  ```


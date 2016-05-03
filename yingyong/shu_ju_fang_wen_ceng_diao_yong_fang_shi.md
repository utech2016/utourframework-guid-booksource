# 3.3 数据访问层调用方式
架构中的数据访问都是按照业务划分在不同的Adapter中, 调用时是根据接口动态生成相应的Adapter实例.
>1. 引用数据访问接口DAInterface项目和业务实体(Entity)项目.
>2. 在[DBCategory.config](configintro/dbcategoryconfigpei_zhi.md)配置文件中配置对应业务单元数据适配器
>3. 在业务逻辑层使用```Utour.Framework.Database.DataAdapterFactory.GetDataAdapter<T>()```方法进行调用
```C#
IUserDataAdapter userDA=DataAdapterFactory.GetInstance().GetDataAdapter<IUserDataAdapter>();
User user = userDA.Load(Id);
 ```


# 3.3.数据访问层调用方式
架构中的数据访问都是按照业务划分在不同的Adapter中, 调用时是根据接口动态生成相应的Adapter实例.
>1. 引用数据访问接口DAInterface和业务实体(Entity)项目.
>2. 对数据适配器进行
>3. 数据库访问调用Utour.Framework.Database.DataAdapterFactory类中GetDataAdapter<T>()方法.
    IUserDataAdapter userDA =                                                                                 DataAdapterFactory.GetInstance().GetDataAdapter<IUserDataAdapter>();
    User user = userDA.Load(Id);


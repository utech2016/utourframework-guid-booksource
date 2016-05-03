# 数据适配器配置(DBCategoryConfig)

数据适配器类配置，对应配置文件DBCategory.config,在此配置项目中所有实现业务数据库适配器接口的适配器类，在用```DataAdapterFactory```调用对应适配器接口实例时，框架会根据此配置动态注入生成对应适配器实例

### 配置结构及样例
```xml
<?xml version="1.0" encoding="utf-8"?>
<!--数据库数据适配器配置，每一个数据适配器都需要在此进行配置-->
<DBCategoryConfig>
  <DataAdapters>
   <!--数据适配器,在这里配置已经实现某一业务数据接口的适配实例
  name：业务单元名称，如业务适配器类名称为UserDataAdaperForSqlServer（业务单元名称 + DataAdapter 
        For数据库类别）则name应配置为 User
  dbCategory:数据库类别，可选类别有:SqlServer,MySql,Oracle,Access,MongoDB
  accessType：数据访问方式，可选方式：ADO,LinqToSql,EF
  -->
    <DataAdapter name="User" dbCategory="SqlServer" accessType="ADO"/>
    <DataAdapter name="Department" dbCategory="SqlServer" accessType="ADO"/>
  </DataAdapters>
</DBCategoryConfig>
```

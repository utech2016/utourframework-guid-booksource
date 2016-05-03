# 数据库提供者配置(DBProviderConfig)
DBProviderConfig 数据库提供者配置类，对应配置文件DBProvider.config,项目所需的所有数据库连接串在此配置文件中配置

### 配置结构及样例
```xml
<?xml version="1.0" encoding="utf-8"?>
<!--数据库连接配置，同一种category只能对应一个DBProvider配置，不得重复出现，数据库连接串请在对应DBConnections节点下添加-->
<DBProviderConfig>
  <DBProviders>
    <!--数据库提供配置，category：数据库类别，可选类别有:SqlServer,MySql,Oracle,Access,MongoDB-->
    <DBProvider category="SqlServer">
      <DBConnections>
        <!--name:数据库连接名称，connection:数据库连接串-->
        <DBConnection name="DemoDB_Write" connection="Data Source=.;Database=UtourDemoDB;User ID=sa;Password=******"/>
      </DBConnections>
    </DBProvider>
  </DBProviders>
</DBProviderConfig>
```

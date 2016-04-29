# 4.1 DBProviderConfig配置
DBProviderConfig，集中数据库连接串配置

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--数据库连接配置，同一种category只能对应一个DBProvider配置，不得重复出现，数据库连接串请在对应DBConnections节点下添加-->
<DBProviderConfig>
  <DBProviders>
    <!--数据库提供配置，category：数据库类别，可选类别有:SqlServer,MySql,Oracle,Access,MongoDB-->
    <DBProvider category="SqlServer">
      <DBConnections>
        <!--name:数据库连接名称，connection:数据库连接串-->
        <DBConnection name="" connection=""/>
      </DBConnections>
    </DBProvider>
  </DBProviders>
</DBProviderConfig>
```

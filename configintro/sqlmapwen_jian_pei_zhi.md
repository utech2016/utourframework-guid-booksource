## SqlMap文件配置
框架将把所有DAO操作的Sql语句统一按照一定业务单元或模块进行配置和管理，每个业务单元DAO操作对应有自己的sqlmap配置

###置结构及样例

```xml
<?xml version="1.0" encoding="utf-8" ?>
<!--SqlMap配置文件，建议按照业务功能模块进行配置-->
<SqlMap>
  <SqlMapConfigurationList>
    <SqlMapDetail>
      <!--sql名称，建议按照某一个数据库操作方法的命名，如AddUser,AddOrder-->
      <SqlName>Add</SqlName>
      <!--Sql语句或存储过程名称-->
      <OriginalSqlString>
        INSERT INTO [UtourDemoDB].[dbo].[User] ([Name] ,[Sex] ,[Birth] ,[Department]) VALUES(@Name,@Sex,@Birth,@Department) 
        </OriginalSqlString>
      <!--数据库连接名称，对应DBConnection中的name属性值-->
      <DBConnectionName>UtourDemoDB_Write</DBConnectionName>
      <!--命令执行类型，Text：sql语句 StoredProcedure：存储过程-->
      <CommandType>Text</CommandType>
    </SqlMapDetail>
  </SqlMapConfigurationList>
  <!--SqlMap名称，建议按照数据适配器类对应配置，如UserDataAdapterForSqlServer,则对应SqlMapName配置为User-->
  <SqlMapName>User</SqlMapName>
</SqlMap>

```

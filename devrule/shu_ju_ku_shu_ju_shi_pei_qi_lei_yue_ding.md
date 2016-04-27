# 2.5.数据库数据适配器类约定
数据适配器类定义在```Utour.DemoDataService.DataAccess```工程内; 数据适配器类是对数据访问接口约定的方法的具体实现, 对数据库的访问操作封装在数据适配器代码内.
>1. 数据访问方式包括Ado.Net, EntityFramework以及LinqToSql三种方式, 每种方式的具体实现都分布在各自的子文件中. 
    >a. Ado.Net数据访问方式采用sqlmap的形式, 将sql相关信息统一置于SqlMap子文件夹下的\*.sqlmap文件中, 使用```Utour.Framework.Database.SqlMapHelper```类进行数据操作.
    >b. EntityFramework数据访问方式采用Code First模式, 使用DbContext的自定义派生类进行数据库操作.
    >c. LinqToSql数据访问方式包含两种子方式: 一种是经典的添加dbml文件, 将文件归置于dbml文件夹下; 另一种是采用XmlMappingSource映射的形式, 将数据库表结构统一置于XmlSource文件夹下的\*.mapping.xml文件中, 并在DataModel文件中创建对应的数据实体模型, 使用```Utour.Framework.Database.LinqToSqlHelper```类进行数据操作, 数据实体模型必须从IDataEntity接口继承.
>2. 数据访问实现类, 需要从```DataAdapterBase```基类, ```Framework.Database.IDataAdapter```和对应的数据访问接口继承. 不同数据访问方式中的实现类的命名空间各有不同, 分别为: ```Utour.DemoDataService.DataAccess.ADO,Utour.DemoDataService.DataAccess.LinqToSql```, ```Utour.DemoDataService.DataAccess.EF```.
>3. 同一数据访问接口对应的多个数据适配器, 一般为对同一数据访问接口在不同种数据库上的实现.
例如: ```UserDataAdaperForSqlServer```和```UserDataAdaperForMySql```分别对应```IUserDataAdapter```接口在SqlServer和MySql数据库上的实现
>4. 数据适配器类名称格式为: 业务单元名称 + DataAdapter + For数据库类型
>5. Sqlmap文件名称格式为: 业务单元名称.sqlmap
>6. XmlSource文件名称格式为: DataModel类型名称.mapping.xml


# 示例项目结构

###源代码存放目录结构
![源代码存放目录结构](../images/img3.png)
![dll输出目录](img4.png)

1. demo.utour.com
   >站点目录
2. demologicservice.utour.com
   >逻辑层服务项目目录
3. demodataservice.utour.com
   >数据层服务项目目录
4. damoapi.utour.com
   >WebApi项目
5. Utour-Bins
  >所有项目的DLL输出目录 	
6. Utour-Bins/xxx.xxx.com/Debug
   >对应各自项目的Debug版DLL输出目录
7. tour-Bins/xxx.xx.com/Release
   >对应各自项目的Release版DLL输出目录

###项目存放目录结构
![项目存放目录结构](../images/img5.png)

* /demodataservice.utour.com
  >项目父目录
* /demodataservice.utour.com/Utour.DemoDataService.Business
  >业务逻辑实现，在此实现所有业务逻辑操作
* /demodataservice.utour.com/Utour.DemoDataService.DAInterface
    子项目目录
* /demodataservice.utour.com/Utour.DemoDataService.CAInterface
   >CAInterface子项目目录
* /demodataservice.utour.com/Utour.DemoDataService.CacheAccess
  >CacheAccess子项目目录
 

/demodataservice.utour.com/Utour.DemoDataService.Config
Config子项目目录

/demodataservice.utour.com/Utour.DemoDataService.DataAccess
DataAccess子项目目录
/demodataservice.utour.com/Utour.DemoDataService.Entity
Entity子项目目录
/demodataservice.utour.com/Utour.DemoDataService.ServiceHost
ServiceHost子项目目录
/demodataservice.utour.com/Utour.DemoDataService.ServiceInterface
ServiceInterface子项目目录
/demodataservice.utour.com/Utour.DemoDataService.ServiceHost/MonitorFiles: 
监控文件存放目录
/demodataservice.utour.com/Utour.DemoDataService.ServiceHost/MonitorFiles/Config: 
Config文件存放目录
/demodataservice.utour.com/Utour.DemoDataService.ServiceHost/MonitorFiles/SqlMap: 
SqlMap文件存放目录


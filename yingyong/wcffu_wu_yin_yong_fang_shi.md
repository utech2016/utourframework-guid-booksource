# 3.2 WCF服务引用方式
架构中不再使用原生服务的添加服务引用方式, 而是使用动态生成服务代理的方式实现动态代理与服务进行调用
>1. 引用服务接口(ServiceInterface)和服务实体(Entity)的DLL.
>2. 在[ServiceClient.config](../configintro/fu_wu_ke_hu_duan_pei_7f6e28_serviceclientconfig.md)中配置服务地址和其他属性值
>3. 调用```Utour.Framework.Service.ServiceFactory```类中```GetInstance<T>()```方法,例如：
```C#
IUserService userService=ServiceFactory.GetInstance<IUserService>();
User user= userService.LoadUser(Id);
```
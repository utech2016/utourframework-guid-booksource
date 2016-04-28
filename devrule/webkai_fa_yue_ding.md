# 2.9 Web开发约定

Web开发约定主要规定开发人员进行MVC网站开发时而制定的一种默认约定.

>1. Global.asax必须继承抽象类```Utour.Framework.Web.MvcApplicationBase```
>2. 控制器建议继承```Utour.Framework.Web.UtourControllerBase```
>3. Web层禁止引入任何业务逻辑, 仅进行页面逻辑处理和数据展示


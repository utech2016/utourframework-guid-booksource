# 2.9 Web开发约定

Web开发约定主要规定开发人员进行Asp.Net Mvc网站开发时而制定的一种默认约定.

>1. Global.asax必须继承抽象类```Utour.Framework.Web.MvcApplicationBase```
>2. 控制器建议继承```Utour.Framework.Web.UtourControllerBase```
>3. Web层禁止引入任何业务逻辑, 仅进行页面逻辑处理和数据展示

视图页面的样式脚本资源文件统一要在[Version.config配置文件](configintro/js_css_wen_jian_ban_ben_pei_zhi.md)中进行版本控制，在页面引用，采用如下方式：

```C#
  //样式文件引用
  @VersionHelper.StylesRender(virtualpath)
  //脚本文件引用
  @VersionHelper.ScriptsRender(virtualpath)
```
VersionHelper类在```Utour.Framework.Web```中定义




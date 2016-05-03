# js,css版本配置(VersionConfig)

脚本样式文件版本管理配置，对应配置文件Version.config,主要作用，给所有页面引用的js，css自动附加文件请求版本号，防止页面js,css客户端缓存，浏览器无法获取最新版本js,css文件而导致新的js,css无法生效的问题。

配置结构及样例：
```xml
<?xml version="1.0" encoding="utf-8"?>
<VersionConfig>
  <!--样式文件url根路径，此根路径会和StyleBundle节点所有配置为相对路径的networkpath属性值进行拼接，得到每个css的完全请求路径-->
  <StylePath>http://www.aaa.com/css</StylePath>
  <!--脚本文件url根路径，此根路径会和ScriptBundle节点所有配置为相对路径的networkpath属性值进行拼接,得到每个js的完全请求路径-->
  <ScriptPath>http://wwww.aaa.com/js</ScriptPath>
  <StyleBundles>
    <!--样式文件版本配置节点：
          virtualpath：虚拟路径,也可称路径别名，此虚拟路径和IIS虚拟路径不同，此路径可任意定义，
                       可以配置多个相同virtualpath的StyleBundle节点，批量捆绑下载一组css
          networkpath：css文件网络路径，支持相对路径和全路径,{version}为版本号占位参数
              version：版本号，用于替换networkpath中的{version},每次css文件更新则需要更改其版本号
    -->
    <StyleBundle virtualpath="~/css/site" networkpath="/Site.css?v={version}" version="1.0.0"/>
  </StyleBundles>
  <ScriptBundles>
    <!--脚本文件版本配置节点：
          virtualpath：虚拟路径,也可称路径别名，此虚拟路径和IIS虚拟路径不同，此路径可任意定义，
                       可以配置多个相同virtualpath的ScriptBundle节点，批量捆绑下载一组js
          networkpath：js文件网络路径，支持相对路径和全路径,{version}为版本号占位参数
              version：版本号，用于替换networkpath中的{version},每次js文件更新则需要更改其版本号
    -->
    <ScriptBundle virtualpath="~/js/jquery" networkpath="/jquery-1.8.2.js?v={version}" version="1.8.2"/>
    <ScriptBundle virtualpath="~/js/site" networkpath="/Site.js?v={version}" version="1.0.0"/>
  </ScriptBundles>
</VersionConfig>
```

## 如何应用
   只需要在引用css和js视图页面的位置使用如下两行代码即可.
   
    ```C#
      @VersionHelper.StylesRender(virtualpath)
      @VersionHelper.ScriptsRender(virtualpath)
      注：virtualpath为StyleBundle和ScriptBundle节点virtualpath属性值
    ```
# Log4net配置(log4net.config)

框架内置log4net的配置文件，并对log4net进行扩展，目前架构中集成了通用日志记录方法, 监控日志记录方法以及网站和服务的日志记录方法。

###配置结构及样例
```xml
<?xml version="1.0" encoding="utf-8" ?>
<log4net>
  <appender name="CommonInfoFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <file type="log4net.Util.PatternString" value="Logs/Common/info_.log"/>
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="INFO" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineServerIP: %property{ServerIP}%newlineClassName:%class%newlineMessage: %message%newline%newline" />
    </layout>
  </appender>
  <appender name="CommonErrorFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <!--日志文件名开头-->
    <file type="log4net.Util.PatternString" value="Logs/Common/err_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <!--是否追加到文件-->
    <appendToFile value="true" />
    <!--混合使用日期和文件大小变换日志文件名-->
    <rollingStyle value="Composite" />
    <!--日期的格式-->
    <datePattern value="yyyyMMdd" />
    <!--最大变换数量-->
    <maxSizeRollBackups value="100" />
    <!--最大文件大小-->
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineServerIP: %property{ServerIP}%newlineMessage: %message%newlineException:%exception%newline%newline" />
    </layout>
  </appender>
  <appender name="CommonInfoRemotingAppender" type="log4net.Appender.RemotingAppender" >
    <sink value="tcp://127.0.0.1:8091/InfoLoggingSink" />
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="INFO" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lossy value="false" />
    <bufferSize value="0" />
    <onlyFixPartialEventData value="true" />
  </appender>
  <appender name="CommonErrorRemotingAppender" type="log4net.Appender.RemotingAppender" >
    <sink value="tcp://127.0.0.1:8091/ErrorLoggingSink" />
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lossy value="false" />
    <bufferSize value="0" />
    <onlyFixPartialEventData value="true" />
  </appender>
  
  <appender name="AOPFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelRangeFilter">
      <acceptOnMatch value="true" />
      <levelMin value="INFO" />
      <levelMax value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <file type="log4net.Util.PatternString" value="Logs/AOP/aop_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineLoggerName: %logger%newlineID: %property{ID}%newlineType: %property{Type}%newlineMethod: %property{Method}%newlineArgs: %property{Args}%newlineReturn: %property{Return}%newlineElapsedMilliseconds: %property{ElapsedMilliseconds}%newline%newline" />
    </layout>
  </appender>
  <appender name="AOPRemotingAppender" type="log4net.Appender.RemotingAppender" >
    <sink value="tcp://127.0.0.1:8091/AOPLoggingSink" />
    <filter type="log4net.Filter.LevelRangeFilter">
      <acceptOnMatch value="true" />
      <levelMin value="INFO" />
      <levelMax value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lossy value="false" />
    <bufferSize value="0" />
    <onlyFixPartialEventData value="true" />
  </appender>

  <appender name="ServiceRecordFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="TRACE" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <file type="log4net.Util.PatternString" value="Logs/Service/record_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineLevel: %level%newlineDate: %date%newlineClientAddress: %property{ClientAddress}%newlineServerAddress: %property{ServerAddress}%newlineServerName: %property{ServerName}%newlineServiceName: %property{ServiceName}%newlineSessionID: %property{SessionID}%newlineContextID: %property{ContextID}%newlineRequestTime: %property{RequestTime}%newlineReplyTime: %property{ReplyTime}%newlineFunctionName: %property{FunctionName}%newlineInputs: %property{Inputs}%newlineOutputs: %property{Outputs}%newlineReturnValue: %property{ReturnValue}%newline%newline" />
    </layout>
  </appender>
  <appender name="ServiceInfoFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="INFO" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <file type="log4net.Util.PatternString" value="Logs/Service/info_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineClassName:%class%newlineServerName: %property{ServerName}%newlineServerIP: %property{ServerIP}%newlineServiceName:%property{ServiceName}%newlineMessage: %message%newline%newline" />
    </layout>
  </appender>
  <appender name="ServiceErrorFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <file type="log4net.Util.PatternString" value="Logs/Service/err_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineServerName: %property{ServerName}%newlineServerIP: %property{ServerIP}%newlineServiceName:%property{ServiceName}%newlineMessage: %message%newline%newline" />
    </layout>
  </appender>
  <appender name="ServiceRecordRemotingAppender" type="log4net.Appender.RemotingAppender" >
    <sink value="tcp://127.0.0.1:8091/ServiceRecordLoggingSink" />
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="TRACE" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lossy value="false" />
    <bufferSize value="0" />
    <onlyFixPartialEventData value="true" />
  </appender>
  <appender name="ServiceRemotingAppender" type="log4net.Appender.RemotingAppender" >
    <sink value="tcp://127.0.0.1:8091/ServiceCommonLoggingSink" />
    <filter type="log4net.Filter.LevelRangeFilter">
      <acceptOnMatch value="true" />
      <levelMin value="INFO" />
      <levelMax value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lossy value="false" />
    <bufferSize value="0" />
    <onlyFixPartialEventData value="true" />
  </appender>
  <appender name="WebInfoFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="INFO" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <file type="log4net.Util.PatternString" value="Logs/Web/info_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineLoggerName: %logger%newlineServerIP: %property{ServerIP}%newlineClientIP: %property{ClientIP}%newlineFromUrl: %property{FromUrl}%newlineReferUrl: %property{ReferUrl}%newlineUniqueID: %property{UniqueID}%newlineServerName: %property{ServerName}%newlineRequestHost: %property{RequestHost}%newlineMessage: %message%newline%newline" />
    </layout>
  </appender>
  <appender name="WebErrorFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <file type="log4net.Util.PatternString" value="Logs/Web/err_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineLoggerName: %logger%newlineServerIP: %property{ServerIP}%newlineClientIP: %property{ClientIP}%newlineFromUrl: %property{FromUrl}%newlineReferUrl: %property{ReferUrl}%newlineUniqueID: %property{UniqueID}%newlineServerName: %property{ServerName}%newlineRequestHost: %property{RequestHost}%newlineMessage: %message%newlineException:%exception%newline%newline" />
    </layout>
  </appender>
  <appender name="WebRecordFileAppender" type="log4net.Appender.RollingFileAppender,log4net">
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="TRACE" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <file type="log4net.Util.PatternString" value="Logs/Web/record_.log"/>
    <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
    <preserveLogFileNameExtension value="true"/>
    <staticLogFileName value="false" />
    <appendToFile value="true" />
    <rollingStyle value="Composite" />
    <datePattern value="yyyyMMdd" />
    <maxSizeRollBackups value="100" />
    <maximumFileSize value="10MB" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%newline%newlineDate: %date%newlineLoggerName: %logger%newlineServerIP: %property{ServerIP}%newlineClientIP: %property{ClientIP}%newlineFromUrl: %property{FromUrl}%newlineReferUrl: %property{ReferUrl}%newlineUniqueID: %property{UniqueID}%newlineServerName: %property{ServerName}%newlineRequestHost: %property{RequestHost}%newlineMessage: %message%newlineException:%exception%newline%newline" />
    </layout>
  </appender>
  <appender name="WebRemotingAppender" type="log4net.Appender.RemotingAppender" >
    <sink value="tcp://127.0.0.1:8091/WebCommonLoggingSink" />
    <filter type="log4net.Filter.LevelRangeFilter">
      <acceptOnMatch value="true" />
      <levelMin value="INFO" />
      <levelMax value="ERROR" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lossy value="false" />
    <bufferSize value="0" />
    <onlyFixPartialEventData value="true" />
  </appender>
  <appender name="WebRecordRemotingAppender" type="log4net.Appender.RemotingAppender" >
    <sink value="tcp://127.0.0.1:8091/WebRecordLoggingSink" />
    <filter type="log4net.Filter.LevelMatchFilter">
      <levelToMatch value="TRACE" />
    </filter>
    <filter type="log4net.Filter.DenyAllFilter" />
    <lossy value="false" />
    <bufferSize value="0" />
    <onlyFixPartialEventData value="true" />
  </appender>
  
  <!--
   框架总体使用下面配置的四类logger，每个logger都有对应的使用场景
   在每个logger下面appender-ref节点，我们可以引用上面定义的各种appender 
   name要和上面的一一对应
   XXXXInfoFileAppender：输出INFO级别的日志到本地文件中
   XXXXErrorFileAppender:输出ERROR级别的日志到本地文件中
   XXXInfoRemotingAppender：远程调用日志服务，通过日志服务将INFO级别的日志输出到MongoDB中
   XXXErrorRemotingAppender：远程调用日志服务，通过日志服务将ERROR级别的日志输出到MongoDB中
   XXXRecordRemotingAppender：远程调用日志服务，通过日志服务将框架的服务和网站上下文信息输出到MongoDB中
  -->
  
  <!--
   Utour.Framework.Log.CommonLogger 在非站点或服务中记录日志使用
  -->
  <logger name="Utour.Framework.Log.CommonLogger">
    <level value="ALL" />
    <appender-ref ref="CommonInfoFileAppender" />
    <appender-ref ref="CommonErrorFileAppender" />
    <appender-ref ref="CommonInfoRemotingAppender" />
    <appender-ref ref="CommonErrorRemotingAppender" />
  </logger>

  <!--
   Utour.Framework.Log.AOPLogger 切面日志，用于开发检测方法执行前后日志
   一般在生产环境不会使用
  -->
  <logger name="Utour.Framework.Log.AOPLogger">
    <level value="ALL" />
    <appender-ref ref="AOPFileAppender" />
    <appender-ref ref="AOPRemotingAppender" />
  </logger>
  
  <!--
   Utour.Framework.Log.ServiceLogger 在wcf服务中记录日志使用
  -->
  <logger name="Utour.Framework.Log.ServiceLogger">
    <level value="ALL" />
    <appender-ref ref="ServiceRecordFileAppender" />
    <appender-ref ref="ServiceInfoFileAppender" />
    <appender-ref ref="ServiceErrorFileAppender" />
    <appender-ref ref="ServiceRemotingAppender" />
    <appender-ref ref="ServiceRecordRemotingAppender"/>
  </logger>
  <!--
   Utour.Framework.Log.WebLogger 在站点下记录日志使用
  -->
 <logger name="Utour.Framework.Log.WebLogger">
    <level value="ALL" />
    <appender-ref ref="WebInfoFileAppender" />
    <appender-ref ref="WebErrorFileAppender"/>
    <appender-ref ref="WebRemotingAppender" />
    <appender-ref ref="WebRecordFileAppender" />
    <appender-ref ref="WebRecordRemotingAppender"/>
  </logger>

</log4net>

```
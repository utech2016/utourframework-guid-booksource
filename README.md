
# 介绍

Utour Framework是一个基于.net 4.0的互联网应用程序开发框架, 同时对一系列代码规范进行约定, 从而使开发人员在进行高效开发的同时, 做到代码易管理易维护易分析易审核, 并确保互联网应用程序的底层实现安全稳定的运行

Utour Framework是基于互联网应用程序常见的三层架构, 并借鉴面向接口开发的优点, 结合我们业务开发的实际情况量身打造而成. 各个层都拥有自己的实体类使层自身的独立性增强, 层与层之间使用接口交互使耦合度大大降低, 并使同一业务逻辑对多种实现方式的支持成为可能.

架构对WCF的发布方式和引用方式进行统一封装, 集中解决了传统WCF配置混乱易错, 发布和引用方式不统一导致的连接效率低下的问题. 同时, 发布方式的统一封装使所有的服务天生自带报文收发日志, 无需开发人员进行另外开发.

架构将项目对web.config的依赖作用削弱至最低, 仅仅配置最基本的节点, 将其他配置按类别集中归置到特定区域, 并进行实时监控, 实现了动态配置, 大大方便和简化了配置过程. 使用Redis来保存Session, 解决网站重启Session丢失的问题和Session无法跨域传递的问题.

还有一些功能模块诸如日志模块, AOP模块等的引入, 使开发人员在此架构中的开发和调试效率得到提高. 












  






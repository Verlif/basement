# Verlif的地下室

## 说明

这里是Verlif的地下室，里面可能乱糟糟的，什么都有。 
不过这些都不重要，有趣最重要。

在Verlif的仓库中，提供的开源工具（以下称为“组件”）包括了：

* `Spring Boot`组件
* `Java`一般组件

这些都可以在`GitHub`中找到，并允许通过`Maven`或是`Gradle`等的构建工具将这些小东西添加到自己的项目中。

## 设计原则

对于这些组件的设计，我个人遵循的是低设计与高扩展原则。当然，这也只是我的设想，执行程度与我的代码能力正相关。  
特征包括了：

* 只做基础功能。不会有复合功能类似于的工具箱这类的依赖在组件中出现。
* 与业务无关。这点也是最重要的，所有的组件都必须轻松兼容绝大部分项目。
* 低依赖。尽量不使用三方依赖，这点主要是减少组件体量与提供功能拓展。
* 自定义化。每个组件都允许便捷地修改核心逻辑来配置自己的业务。

## 总列表

### Spring Boot 组件

* 全局异常处理 [exception-spring-boot-starter](https://github.com/Verlif/exception-spring-boot-starter)
  * 全局异常处理的组件化实现。
  * 不需要再在一个advice中写所有的异常处理了，现在只需要通过实现处理接口，异常处理器就会将对应的异常交由这个处理器处理。
* 接口限制器 [limit-spring-boot-starter](https://github.com/Verlif/limit-spring-boot-starter)
  * 只需要一个注解即可对接口进行访问控制。
  * 不同的接口允许不同的限制器来管理。
* 基础日志与接口日志服务 [logging-spring-boot-starter](https://github.com/Verlif/logging-spring-boot-starter)
  * 一个注解完成接口日志，一个接口管理基础日志服务。
  * 可配置的接口日志的处理。
* 接口权限服务 [permission-spring-boot-starter](https://github.com/Verlif/permission-spring-boot-starter)
  * 一个注解实现对接口的访问权限控制。
  * 与业务无关。适用于任何项目，无论是否有数据库，无论用户数据结构。
* 定时任务服务 [task-spring-boot-starter](https://github.com/Verlif/task-spring-boot-starter)
  * 通过注解完成定时任务。
  * 动态添加或关闭定时任务。
  * 可配置的定时任务名单。
* 文件管理系统 [file-spring-boot-starter](https://github.com/Verlif/file-spring-boot-starter)
  * 字节流或是Base64类型的文件上传与下载
  * 文件的分页查询

### Java 组件

* 简单指令生成器 [just-simmand](https://github.com/Verlif/just-simmand)
  * 将任意的实例对象转换为一个指令组，其中的指令就是其拥有的公共方法。
* Jackson序列化脱敏 [jackson-sensible](https://github.com/jackson-sensible)
  * 使用便利的Jackson序列化的数据脱敏。
  * 支持几乎所有的数据类型（通过处理选择器中的脱敏处理器来实现，若内置的数据类型不足，可自行添加）。
* 参数解析器 [param-parser](https://github.com/param-parser)
  * 将String类型转换为其他数据类型的解析器。
  * 为其他组件提供数据转换支持。
* Jar文件加载器 [loader-jar](https://github.com/loader-jar)
  * 将Jar文件中的指定类的实例或其实现类提取出来。
  * 像是动态模组化的功能就可以使用，类似于游戏打mod。
* Socket消息交互 [socket-core](https://github.com/socket-core)
  * 内置了Server与Client用于简单的信息交互。
* Socket指令交互 [socket-command](https://github.com/socket-command)
  * 组合`socket-core`与`loader-jar`的一个多端指令系统
  * Server可以加载数个Jar文件作为指令集，并能在运行时再添加或关闭指令。

## 版本说明

组件的依赖版本基于多方面因素确定，非常主观。一般情况下分为以下类型

|  前缀   | 说明                    |
|:-----:|:----------------------|
| test  | 用于测试，其结构、功能、用途等都可能会变动 |
| beta  | 确定了组件的功能与结构，但未经功能测验   |
| alpha | 完成了一般的功能测验，但稳定性未知     |
|   无   | 发布版，稳定性尚可             |

## 关于ISSUE

如果您对组件有任何的疑问，可以在对应的仓库中添加`issue`。  
如果您有一些想要分享的想法，可以在本仓库中添加`issue`。

## 写在最后

这些组件完全由自己的兴趣为基础开发的，所以需求、设计可能与实际项目上不匹配，这些都会在后续的更新中慢慢优化。  
没有讨论群、没有二维码、没有官网。
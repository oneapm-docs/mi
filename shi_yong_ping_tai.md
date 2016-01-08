# 使用平台

## 1. 配置 Ant

* 第一步：下载最新的 OneAPM Android SDK

* 第二步：添加 oneapm-android-agent.jar 到工程 libs 目录中，如果项目中没有 libs 目录，请创建一个新的 libs 目录

* 第三步：设置 ANT_OPTS 环境变量

**Mac OS / Linux 环境**

`export ANT_OPTS="-javaagent:/path/to/oneapm/class.rewriter.jar"`

**Windows 环境**


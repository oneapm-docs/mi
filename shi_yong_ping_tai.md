# 使用平台

## 1. 配置 Ant

* 第一步：下载最新的 OneAPM Android SDK

* 第二步：添加 oneapm-android-agent.jar 到工程 libs 目录中，如果项目中没有 libs 目录，请创建一个新的 libs 目录

* 第三步：设置 ANT_OPTS 环境变量

**Mac OS / Linux 环境**

`export ANT_OPTS="-javaagent:/path/to/oneapm/class.rewriter.jar"`

**Windows 环境**

* 方法一：“在我的电脑右键->属性->高级系统设置->环境变量->添加环境变量”，如下图: 

![Ant]安装(ant_opts(03-20-10-21-34)-1426824126.png)


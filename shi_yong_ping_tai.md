# 使用平台

## 1. 配置 Ant

* 第一步：下载最新的 OneAPM Android SDK

* 第二步：添加 oneapm-android-agent.jar 到工程 libs 目录中，如果项目中没有 libs 目录，请创建一个新的 libs 目录

* 第三步：设置 ANT_OPTS 环境变量

**Mac OS / Linux 环境**

`export ANT_OPTS="-javaagent:/path/to/oneapm/class.rewriter.jar"`

**Windows 环境**

* 方法一：“在我的电脑右键->属性->高级系统设置->环境变量->添加环境变量”，如下图: 

![Ant安装](ant_opts(03-20-10-21-34)-1426824126.png)

其中 “/path/to/oneapm/”请用你实际存放 OneAPM 的 class.rewriter.jar 的路径替换。

不要放在工程的 libs 目录中！

* 方法二：在命令行中设置

`set ANT_OPTS="-javaagent:/path/to/oneapm/class.rewriter.jar"`

**注意**：请勿将该环境变量 ANT_OPTS 永久设置到用户或系统环境变量里，否则会影响其他不需要进行嵌码的 Android 项目。建议在单次编译的命令行状态下临时设置该环境变量，或单独在需要嵌码项目的批处理编译脚本中设置该环境变量。

## 2. 设置 App 权限















# Ant安装方式

## 1. 配置 Ant
* 第一步：命名你的应用程序，获取对应的Token值。

* 第二步：下载最新的 [OneAPM Android SDK](https://user.oneapm.com/account/agent/android/download.do?version=latest)

* 第三步：添加 oneapm-android-agent.jar 到工程 libs 目录中，如果项目中没有 libs 目录，请创建一个新的 libs 目录

* 第四步：设置 ANT_OPTS 环境变量

**Mac OS / Linux 环境**

`export ANT_OPTS="-javaagent:/path/to/OneAPM_Android_Ant_{VERSION}/class.rewriter.jar"`

**Windows 环境**

`set ANT_OPTS="-javaagent:/path/to/OneAPM_Android_Ant_{VERSION}/class.rewriter.jar"`

**注意**：请勿将该环境变量 ANT_OPTS 永久设置到用户或系统环境变量里，否则会影响其他不需要进行嵌码的 Android 项目。建议在单次编译的命令行状态下临时设置该环境变量，或单独在需要嵌码项目的批处理编译脚本中设置该环境变量。

### 2. 配置授权信息

确保应用程序的 AndroidManifest.xml 配置文件中，引入了以下授权：

```
<!--发送性能数据到服务器需要该权限--> 
<uses-permission android:name="android.permission.INTERNET" /> 
<!--发送性能数据到服务器需要该权限--> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
<!--sdk读取设备识别码需要该权限--> 
<uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
<!--【非必选】若想知道 Crash 的时候，后台有哪些任务运行，请引入该权限--> 
<uses-permission android:name="android.permission.GET_TASKS" />
```
注意：如果您的应用使用 proguard 混淆，请配置以下：

```
-keep class org.apache.http.impl.client.** 
-dontwarn org.apache.commons.** 
-keep class com.blueware.** { *; } 
-dontwarn com.blueware.** 
-keep class com.oneapm.** {*;} 
-dontwarn com.oneapm.** 
-keepattributes Exceptions, Signature, InnerClasses
```

注意：如果您希望保留行号信息，建议您在 proguard.cfg 中添加如下代码：

```
-keepattributes SourceFile, LineNumberTable
```





静候 5 分钟后，若无应用程序相关性能数据展现，或安装过程中出现问题：请联系 OneAPM 客服人员：

* 技术咨询热线： 400-622-3101

* 销售咨询热线： 400-659-1230

* OneAPM 客服邮箱：support@oneapm.com

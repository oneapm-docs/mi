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
## 3. 用户信息配置（可选）
顾名思义，就是说和每一个用户相关联的数据信息。例如崩溃的时候可以根据这个配置查询是哪一个用户发生了崩溃。如下：

```
// 附加数据 
HashMap<String,String> extraData = new HashMap<String, String>(); 
String userTel = "15801388723"; 
extraData.put("tel", userTel); 
extraData.put("userId", "888"); 
extraData.put("email", "88888@qq.com"); 

ContextConfig config = new ContextConfig(); 
String searchValue = userTel; 
config.setSearchValue(searchValue); // 设置一个搜索值 
config.setExtra(extraData); 

OneApmAgent.init(this.getApplicationContext()).setContextConfig(config).setToken("---<YOU TOKEN HERE>---").start(); 
```
## 4. 集成统计分析功能（可选）
在每个 Activity 中导入 OneApmAnalysis 类
``` 
import com.oneapm.agent.android.module.analysis.AnalysisModule; 
```
在每个 Activity 的 onResume() 方法中添加代码:
```
AnalysisModule.onResume();
```
如下示例代码：
```
@Override
protected void onResume() {
  super.onResume();
  AnalysisModule.onResume();
}
```
在每个 Activity 的 onPause() 方法中添加代码:
```
AnalysisModule.onPause();
```
如下示例代码：
```
@Override
protected void onPause() {
  super.onPause(); 
  AnalysisModule.onPause();
}
```
配置渠道信息:
如果您的app需要增加渠道信息请在AndroidManifest.xml的Application标签内添加如下（请把YOU CHANNEL替换成您自己的发布渠道例如豌豆荚、360等）
```
<meta-data android:name ="BluewareChannel" android:value="YOUR CHANNEL" />
```
*注意：如果两个Activity是继承关系，只需要在父Activity添加即可，如果在两个Activity中同时添加，则会造成重复统计。
*

### 5. 功能开关（可选）
如果您想使用帧率监控功能可以配置如下代码开启帧监控功能

```
PerformanceConfiguration.getInstance().setEnableFps(true);
```

### 6.启动Agent

在默认启动的 Activity 中 import OneApmAgent类
```
import com.oneapm.agent.android;
```
在App的第一个Activity的 onCreate() 方法中加入如下调用代码来初始化 OneAPM（其中包含了在步骤 2 中根据应用程序名称而生成的授权编号）
```
OneApmAgent.init(this.getApplicationContext()).setToken("---<YOU TOKEN HERE>---").start();
```
或如果设置了用户信息（第5步），初始化代码如下（config是类似第5步中的用户信息配置）

```
OneApmAgent.init(this.getApplicationContext()).setContextConfig(config).setToken("---<YOU TOKEN HERE>---").start();

```

###  7. 验证是否成功集成探针
在Logcat中过滤oneapm标签，查看是否有类似如下的日志输出即可(VERSION代表发布版本，因版本不同而不同)。

```
OneAPM started with version :{VERSION}.

```

### 8. 静候 5 分钟，开启 OneAPM 之旅

静候 5 分钟，等待应用程序向 OneAPM 发送应用程序性能数据，即可开始使用 OneAPM 应用性能管理。

若应用程序无数据展现，或安装过程中有任何问题:

您可以采取以下方式与我们取得联系：

* 技术咨询热线： 400-622-3101

* 销售咨询热线： 400-659-1230

* OneAPM 客服邮箱：support@oneapm.com

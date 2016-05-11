# Maven 插件安装方法

## 1.命名你的应用程序

 点击进入OneAPM Mobile Insight[集成安装界面](https://mi.oneapm.com/mobile/app/setup#/)，命名应用程序。

## 2.配置Maven
*下面配置使用到的PLUGIN_VERSION，需要替换成解压后相应的版本号。例如：下载版本为OneAPM_Android_Maven_2.0.1，需将PLUGIN_VERSION设置为2.0.1。*

下载maven插件包解压，假设解压之后的路径是PATH_TO_ONEAPM_MAVEN_PATH 后续会用到；解压之后会有3个.jar文件一个.pom文件，这些文件下面的操作步骤会用到。

[OneAPM_Android_Maven_Plugin.zip](https://user.oneapm.com/account/agent/maven/download.do?version=latest)

* 1、注册解压后文件夹中的jar包为本地maven库

**注册 oneapm-android-agent.jar**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=agent.android -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH/oneapm-android-agent.jar`

**注册 class.rewriter.jar**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=class.rewriter -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH/class.rewriter.jar`

* 2.注册 oneapm-android-maven-plugin.jar和plugin.maven.pom *

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=plugin.maven -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH\plugin.maven.jar -DpomFile=PATH_TO_ONEAPM_MAVEN_PATH\plugin.maven.pom`

**例如，配置一个例子：**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=plugin.maven -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=E:\agent\gitlab\android-maven-plugin\target\plugin.maven.jar -DpomFile=E:\agent\gitlab\android-maven-plugin\target\plugin.maven.pom`

**注意：-Dfile=这个后面一定不要有空格，否则运行 Maven 会报错！！！**

* 3、配置本地 pom.xml 文件，添加刚才注册的 jar 包，如下依赖： 

```
<dependency>
<groupId>com.oneapm.agent.android</groupId>
<artifactId>agent.android</artifactId>
<version>1.0.8</version>
</dependency>
插件: 
<plugin> 
<groupId>com.oneapm.agent.android</groupId> 
<artifactId>plugin.maven</artifactId>
<version>1.0.8</version>
<executions>
<execution>
<goals>
<goal>instrument</goal>
</goals>
</execution>
</executions>
</plugin>
```
完整如下：

```
<groupId>xxx.yyy.zzzz</groupId>
<artifactId>TestMavenAndroid02</artifactId>
<version>1.0</version>
<packaging>apk</packaging>
<dependencies>
<dependency>
<groupId>com.google.android</groupId>
<artifactId>android</artifactId>
<version>4.1.1.4</version>
<scope>provided</scope>
</dependency>
<dependency>
<groupId>com.oneapm.agent.android</groupId>
<artifactId>agent.android</artifactId>
<version>1.0.8</version>
</dependency>
</dependencies>
<build>
<finalName>${project.artifactId}</finalName>
<sourceDirectory>src</sourceDirectory>
<plugins>
<plugin>
<groupId>com.jayway.maven.plugins.android.generation2</groupId>
<artifactId>android-maven-plugin</artifactId>
<version>4.0.0-rc.2</version>
<configuration>
<sdk>
<platform>19</platform>
</sdk>
<manifest>
<debuggable>true</debuggable>
</manifest>
</configuration>
<extensions>true</extensions>
</plugin>
<plugin>
<groupId>com.oneapm.agent.android</groupId>
<artifactId>plugin.maven</artifactId>
<version>1.0.8</version>
<executions>
<execution>
<goals>
<goal>insstrument</goal>
</goals>
</execution>
</executions>
</plugin>
</plugins>
</build>
```

## 3. 配置授权信息

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

## 4.WebView 性能监控（可选）

如果你需要开启此功能，请参考 [WebView 性能监控使用说明](https://oneapm.kf5.com/posts/view/45662/?_ga=1.103647751.624652157.1461721958)。

## 5. 用户信息配置（可选）
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
## 6. 集成统计分析功能（可选）
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
注意：如果两个Activity是继承关系，只需要在父Activity添加即可，如果在两个Activity中同时添加，则会造成重复统计。
## 7. 功能开关（可选）
如果您想使用帧率监控功能可以配置如下代码开启帧监控功能

```
PerformanceConfiguration.getInstance().setEnableFps(true);
```

## 8.启动Agent

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

##  9. 验证是否成功集成探针
在Logcat中过滤oneapm标签，查看是否有类似如下的日志输出即可(VERSION代表发布版本，因版本不同而不同)。

```
OneAPM started with version :{VERSION}.

```


## 10. 静候 5 分钟，开启 OneAPM 之旅

静候 5 分钟，等待应用程序向 OneAPM 发送应用程序性能数据，即可开始使用 OneAPM 应用性能管理。

若应用程序无数据展现，或安装过程中有任何问题:

您可以采取以下方式与我们取得联系：

技术支持热线：400-622-3101    
OneAPM 客服邮箱：support@oneapm.com
OneAPM MI技术交流3群：471152223
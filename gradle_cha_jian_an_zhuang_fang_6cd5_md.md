# Android SDK - Gradle 插件安装方法

1. 命名应用程序并获取 App token

  点击进入OneAPM Mobile Insight[集成安装界面](https://mi.oneapm.com/mobile/app/setup#/)，命名应用程序。

2. [下载并解压 OneAPM SDK](https://user.oneapm.com/account/agent/gradle/download.do?version=latest)

3. 配置 Gradle
首先我们将 plugin 文件夹整体拷贝到项目根目录, 具体如下图所示
![](A113.jpg)

打开工程根目录下的 build.gradle 文件。
  ![](A114.jpg)

第二步：在 dependencies 模块中加入代码。

```java
classpath fileTree(dir: 'plugin', include: ['*.jar'])
```

![](A115.jpg)

引入 OneAPM

将agent文件夹下的 oneapm-android-agent.jar 文件拷贝至项目libs目录下(如没有此目录请自行创建)
![](A116.jpg)
打开主模块目录下的 build.gradle 文件。
![](A117.jpg)

在文件头部引入 OneAPM。

```java
apply plugin: 'oneapm'
```
![](A118.jpg)
如此即完成了OneAPM的引入。

5.rebuild & clean 项目

建议 rebuild & clean 项目，来确保 OneAPM 配置生效。

如果 dependencies 没有如下的配置

    ```compile fileTree(include: ['*.jar'], dir: 'libs')```

请在 dependencies 中加入如下配置

    ```compile files('libs/oneapm-android-agent.jar')```


6.配置授权信息

确保应用程序的 AndroidManifest.xml 配置文件中，引入了以下授权：

```xml
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
```-keep class org.apache.http.impl.client.** 
-dontwarn org.apache.commons.** 
-keep class com.blueware.** { *; } 
-dontwarn com.blueware.** 
-keep class com.oneapm.** {*;} 
-dontwarn com.oneapm.** 
-keepattributes Exceptions, Signature, InnerClasses```

若想使用 Crash 快照功能，请引入以下授权信息：

```xml
<uses-permission android:name="android.permission.GET_TASKS" />
```
注意：如果您希望保留行号信息，建议您在 proguard.cfg 中添加如下代码：
```-keepattributes SourceFile, LineNumberTable```

如果使用基站定位，请添加如下权限：

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

注意：如果您的应用使用 progurd 混淆，请配置以下：

```
 -dontwarn org.apache.commons.**
 -keep class org.apache.http.impl.client.**
 -dontwarn org.apache.commons.**
 -keep class com.blueware.** { *; }
 -dontwarn com.blueware.**
 -keepattributes Exceptions, Signature, InnerClasses
```

注意：如果您希望保留行号信息，建议您在 proguard.cfg 中添加如下代码：

```
- keepattributes SourceFile ,LineNumberTable
```

7.启动 Agent

在默认 Activity 中 import BlueWare 类：

```java
import com.blueware.agent.android.BlueWare;
```

在 onCreate() 方法中加入如下 call 来初始化 oneAPM（其中包含了在步骤 2 中根据应用程序名称而生成的授权编号）：

```java
BlueWare.withApplicationToken(
"<use app token created at step 1>")
.start(this.getApplication());
```

8.启动应用程序

clean project，并重新在模拟器或设备中启动应用程序，开始应用性能管理。

9.静候 5 分钟，开启 OneAPM 之旅

静候 5 分钟，等待应用程序向 OneAPM 发送应用程序性能数据，即可开始使用 OneAPM 应用性能管理。

若应用程序无数据展现，或安装过程中有任何问题:

您可以采取以下方式解决问题：

* 
技术支持热线：400-622-3101

*     
OneAPM 客服邮箱：support@oneapm.com
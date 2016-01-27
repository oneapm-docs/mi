# Eclipse 插件安装方法

## 1. 安装 SDK


* 第一步：打开 Eclipse

* 第二步：菜单 Help->Install New Software

![Eclipse安装](eclipse11419579629.png)

* 第三步：添加 OneAPM Android 的 Eclipse 插件源

Eclipse 4.4 之前的版本，请使用：

`https://download.oneapm.com/android_agent/eclipse_lt_4.4/`

Eclipse 4.4 及之后的版本（需要 JDK 1.8），请使用：

`https://download.oneapm.com/android_agent/eclipse_gt_4.4/`

![Eclipse安装](eclipse21419579643.png)

* 第四步：执行添加如下图

![Eclipse安装](QQT20150729174216.jpg)

**提示**：取消勾选 Contact all update during Install to find required software 会提高安装的速度；如果安装失败，重新勾选 Contact all update during Install to find required software，等待安装完成。

## 2. 安装 Agent 到 Project

* 第一步：新建或者在已有 Android Project 工程右键会出现如下：
 
![Eclipse安装](eclipse41419579660.png)

* 第二步：执行安装 OneAPM 插件会自动复制 OneAPM Agent 的 jar 包到工程的 libs 目录。安装成功如下：

![Eclipse安装](eclipse51419579667.png)

**注意**：查看 Android 工程的 libs 目录中，是否有 oneapm-android-agent.jar 文件，如果没有请刷新 libs 目录。

## 3. 配置 Agent

* 第一步：在项目工程右键 Build Path Configure Build Path 将 oneapm-android-agent.jar 添加到系统的 Build Path 中；

![Eclipse安装](eclipse61419579677.png)

* 第二步：在应用的主 Activity 的 class 中，添加

```java
import com.blueware.agent.android.BlueWare;
```

* 第三步：在 onCreate 方法中，添加

```java
BlueWare.withApplicationToken("your token").start(this.getApplication());
```

**注意**：APIKey 由 OneAPM 分发，每个应用对应一个唯一的 APIKey。

## 4. 配置 App 权限

* 第一步：在待监测的 App 工程的 AndroidMainfest.xml 文件中增加以下的权限

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
```

若想使用 Crash 快照功能，请引入以下授权信息：

```xml
<uses-permission android:name="android.permission.GET_TASKS" />
```

如果使用基站定位，请添加如下权限：

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

**注意**：如果应用使用 progurd 混淆，请按如下方式配置

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

静候 5 分钟后，若无应用程序相关性能数据展现，或安装过程中出现问题：请联系 OneAPM 客服人员：

* 技术咨询热线： 400-622-3101

* 销售咨询热线： 400-659-1230

* OneAPM客服邮箱：support@oneapm.com

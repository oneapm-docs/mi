# Android SDK - Gradle 插件安装方法

1. 命名应用程序并获取 App token

    第一步：命名应用程序。

    第二步：复制 App token 的序列码，在接下来的步骤中使用。

2. 下载并解压 OneAPM SDK

到官网下载最新版本的探针
3. 配置 Gradle

    第一步：打开工程根目录下的 build.gradle 文件。

    第二步：在 dependencies 模块中加入代码。

    ```classpath fileTree(dir: 'YourOneAPMPath/oneapm/plugin', include: ['*.jar'])```

4. 引入 OneAPM

    第一步：打开主模块目录下的 build.gradle 文件。

    第二步：在 dependencies 模块中加入代码。

    compile fileTree(dir:'YourOneAPMPath/oneapm/agent',include:['*.jar'])

    第三步：在文件头部引入 OneAPM。

    apply plugin: 'oneapm'

5. rebuild & clean 项目

建议 rebuild & clean 项目，来确保 OneAPM 配置生效。
6.  配置授权信息

确保应用程序的 AndroidManifest.xml 配置文件中，引入了 INTERNET 和 ACCESS_NETWORK_STATE 两个请求授权：

<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

若想使用 Crash 快照功能，请引入以下授权信息：

<uses-permission android:name="android.permission.GET_TASKS" />

注意：如果您的应用使用 progurd 混淆，请配置以下：

 -dontwarn org.apache.commons.**
 -keep class org.apache.http.impl.client.**
 -dontwarn org.apache.commons.**
 -keep class com.blueware.** { *; }
 -dontwarn com.blueware.**
 -keepattributes Exceptions, Signature, InnerClasses

7. 启动 Agent

在默认 Activity 中 import BlueWare 类：

import com.blueware.agent.android.BlueWare;

在 onCreate() 方法中加入如下 call 来初始化 oneAPM（其中包含了在步骤 2 中根据应用程序名称而生成的授权编号）：

BlueWare.withApplicationToken("<generate app token by creating a name above>").start(this.getApplication());

8. 启动应用程序

clean project，并重新在模拟器或设备中启动应用程序，开始应用性能管理。
9. 静候 5 分钟，开启 OneAPM 之旅

静候 5 分钟，等待应用程序向 OneAPM 发送应用程序性能数据，即可开始使用 OneAPM 应用性能管理。

若应用程序无数据展现，或安装过程中有任何问题:

您可以采取以下方式解决问题：

    技术支持热线：400-622-3101

    OneAPM 客服邮箱：support@oneapm.com
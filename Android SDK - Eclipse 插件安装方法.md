# Android SDK - Eclipse 插件安装方法

## 1. 安装 SDK


* 第一步：打开 Eclipse

* 第二步：菜单 Help->Install New Software

![Eclipse安装](Eclipse 安装方法1-1419579629.png)

* 第三步：添加 OneAPM Android 的 Eclipse 插件源

Eclipse 4.4 之前的版本，请使用：

`https://download.oneapm.com/android_agent/eclipse_lt_4.4/`

Eclipse 4.4 及之后的版本（需要 JDK 1.8），请使用：

`https://download.oneapm.com/android_agent/eclipse_gt_4.4/`

![Eclipse安装](Eclipse 安装方法2-1419579643.png)

* 第四步：执行添加如下图

![Eclipse安装](QQͼƬ20150729174216.jpg)

**提示**：取消勾选 Contact all update during Install to find required software 会提高安装的速度；如果安装失败，重新勾选 Contact all update during Install to find required software，等待安装完成。

## 2. 安装 Agent 到 Project

* 第一步：新建或者在已有 Android Project 工程右键会出现如下：
 
![Eclipse安装](Eclipse 安装方法4-1419579660.png)

* 第二步：执行安装 OneAPM 插件会自动复制 OneAPM Agent 的 jar 包到工程的 libs 目录。安装成功如下：

![Eclipse安装](Eclipse 安装方法5-1419579667.png)

**注意**：查看 Android 工程的 libs 目录中，是否有 oneapm-android-agent.jar 文件，如果没有请刷新 libs 目录。

## 3. 配置 Agent

* 第一步：在项目工程右键 Build Path Configure Build Path 将 oneapm-android-agent.jar 添加到系统的 Build Path 中；

![Eclipse安装](Eclipse 安装方法6-1419579677.png)

* 第二步：在应用的主 Activity 的 class 中，添加

`import com.blueware.agent.android.BlueWare;`

* 第三步：在 onCreate 方法中，添加

`BlueWare.withApplicationToken(ApiKey).start(this.getApplication());`

**注意**：APIKey 由 OneAPM 分发，每个应用对应一个唯一的 APIKey。

## 4. 配置 App 权限

* 第一步：在待监测的 App 工程的 AndroidMainfest.xml 文件中增加以下的权限

```
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.GET_TASKS" />
```

**注意**：如果应用使用 progurd 混淆，请按如下方式配置












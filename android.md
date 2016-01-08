# Android

## OneAPM Android SDK 1.0.8

**发布日期：**2015/5/26

**增加功能：**

1.Eclipse 插件更新，支持 Eclipse 4.4 及之后的版本。

修复问题：

    本地没有 ssl 的环境下无法发送 crash 信息；

    在 crash 没发送成功并且积累比较多的时候启动黑屏的 bug；

    Reinstall OneAPM 的时候，没有更新到最新版本；

    Agent 安装过程中，license 信息需要更新；

    在手机没有 sim 卡的时候获取手机设备信息会有异常，造成数据收集异常；

    在特定情况下无法上传数据；

    Agent 的信息需要与用户系统保持一致；

    WebView 自定义 webviewClient 的时候发生 Crash。

## OneAPM Android SDK 1.0.7

**发布日期：**2015/2/14

**增加功能：**

1.慢 trace 和 Crash 添加了 running app 功能；

2.Crash 添加了 Crash 操作路径，便于 bug 的复现；

3.数据传输智能判断是否该使用加密链接；

4.其他一些细节改进。 

## OneAPM Android SDK 1.0.6

**发布日期：**2014/12/22

**修复问题：**

1.重构了 Crash 监测功能、添加了记录崩溃前用户的操作轨迹、Crash 修改状态标识、Crash 影响用户等功能；

2.修复了部分 trace 数据遗漏的问题；

3.解决了 Eclipse 插件版本号提示不对的问题。

## OneAPM Android SDK 1.0.5

**发布日期：**2014/10/9

**修复问题：**

1.解决 trace AsyncTask 的时候 java.lang.ClassCastException 的问题;

2.可以添加 @SkipTrace 来跳过不需要跟踪的 trace;

3.解决了没有 versionCode 定义的时候的崩溃问题;

4.其他小问题的 fix 

## OneAPM Android SDK 1.0.4

** 发布日期：**
2014/8/8

**修复问题：**

1.解决 Java u55、Java 8 的崩溃问题;

2.解决 SDK Instrument Gson 时候的崩溃问题;

3.下载 OneAPM Android SDK 1.0.4;
# Android

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
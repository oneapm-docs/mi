# Android

如何更新最新的 Android SDK ？请查看 Android SDK 更新方法 

## OneAPM Android SDK 2.0.4(Beta)

**发布日期：**2015/11/26

**优化功能：**

 1.增加了Anr监控功能

 2.增加了socket监控功能

 3.增加了android的帧率监控功能

 4.优化了运营商获取方式

 5.优化了webview的兼容性

修复问题：

1.修复了部分bug。

## OneAPM Android SDK 2.0.3

**发布日期：**2015/10/30

**优化功能：**

1.增加在操作系统版本升级时重新连接的功能；

2.优化用户信息查询接口；

3.增加对 okhttp 2.0.3+ 支持；

4.优化探针性能。

**修复问题：**

1.修复网络时间统计 bug。

## OneAPM Android SDK 2.0.2

**发布日期：**2015/9/21

**优化功能：**

1.优化探针对 Cordova 框架，Webview 的支持；

2.优化探针对网宿 SDK 的支持；

3.优化设置页面上传 ProGuard 文件功能；

4.优化日活数据类型，添加 IMEI 信息；

5.优化用户信息模块，允许用户上传长度为256字节以内的用户信息；

6.优化网络请求 trace 数据中 HTTP Request/Response Header 信息的采集。默认设置为不采集，付费用户可设置开启该功能。

**修复问题：**

1.交互 trace 详情中显示联网信息、地理位置、电量、CPU、Root 信息。

**备注：**

启用 WebView 功能需要配置对应的 WebView JavaScript 文件，具体操作请参考文档：WebView 性能监控使用说明。

## OneAPM Android SDK 2.0.1

**发布日期：**2015/7/24

**增加功能：**

1.移动端网络请求与服务端相关联；

2.WebView 模块支持收集 JavaScript 错误。

**修复问题：**

1.修复部分情况下 okhttp 会导致 crash 的问题；

2.修复特定情况下空指针问题。

## OneAPM Android SDK 1.0.8

**发布日期：**2015/5/26

**增加功能：**

1.Eclipse 插件更新，支持 Eclipse 4.4 及之后的版本。

**修复问题：**

1.本地没有 ssl 的环境下无法发送 crash 信息；

2.在 crash 没发送成功并且积累比较多的时候启动黑屏的 bug；

3.Reinstall OneAPM 的时候，没有更新到最新版本；

4.Agent 安装过程中，license 信息需要更新；

5.在手机没有 sim 卡的时候获取手机设备信息会有异常，造成数据收集异常；

6.在特定情况下无法上传数据；

7.Agent 的信息需要与用户系统保持一致；

8.WebView 自定义 webviewClient 的时候发生 Crash。

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
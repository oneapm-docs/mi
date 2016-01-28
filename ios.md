# iOS Release Note
如何更新最新的 iOS SDK ？ [请查看iOS SDK](https://oneapm.kf5.com/posts/view/44278)



## OneAPM iOS smart SDK 2.0.1




## OneAPM iOS smart SDK 2.0.0

**特点**：完全重构版，重写了90%代码。

**内容：**
1. 识别设备类型（iPhone/iPad/iPod、操作系统版本、运营商类型）；
1. 
统计 http 访问情况、出错情况。

**修复问题：**
1. 
与百度地图、极光推送等第三方 SDK 不兼容问题；
1. 
当路由被劫持，访问 ip.taobao 连接成功，但返回数据不合法时，数据无法上报的问题；
1. 
首次安装时重试间隔时间错误。
改进功能：
Agent 自身日志系统改善，统一输出格式，使用[OneAPM printLog:YES］开启或关闭，默认为关闭状态。


**改进功能：**

1. 
Agent 自身日志系统改善，统一输出格式，使用[OneAPM printLog:YES］开启或关闭，默认为关闭状态。

[点击此处下载 iOS smart SDK](https://oneapm.kf5.com/attachments/download/324726/001564c3213991c1c71b682e6be5b26/)


##OneAPM iOS SDK 1.1.3

发布日期：2015/8/27

[下载链接：iOS SDK 1.1.3](https://user.oneapm.com/account/agent/ios/download.do?version=1.1.3&_ga=1.171887072.1942864907.1444901230)

**增加功能：**

1. 
支持监控通过 NSURLSession 发送的 HTTP 请求；
1. 
增加用户自定义信息功能；
1. 
性能优化；

**修复问题：**

1. 
解决 Agent 初始化工程中可能发送 crash 的问题。

**备注：**

新增功能第二条的配置方式如下：

接口信息：
```
+ (void)setCustomInfo:(NSString *)info;
用法示例：
[OneAPM setCustomInfo:@"18611421164"];
[OneAPM startWithApplicationToken:@"225D3C244ACE5E49F1CFA920EF94D8A489"];
通过该接口设置用户识别信息，该信息会和 crash log 等数据关联。 
```
##OneAPM iOS SDK 1.1.2

发布日期：2015/8/4

下载链接：[iOS SDK 1.1.2](https://user.oneapm.com/account/agent/ios/download.do?version=1.1.2)

**增加功能：**

1. 
增加对 SDWebImage 的 HTTP 请求监控；

1. 
其它优化。

**修复问题：**

1. 
解决使用 ASIHttpRequest 时偶发崩溃的问题；
1. 
解决工程名字为中文时捕获的 crash log 包含乱码的问题；

## OneAPM iOS SDK 1.1.1



发布日期：2015/6/9

下载链接：iOS SDK 1.1.1

**修复问题：**
1. 

修改在一些场景中统计的 http 请求不完善的问题。

## OneAPM iOS SDK 1.1.0

发布日期：2015/6/3

下载链接：[iOS SDK 1.1.0](https://user.oneapm.com/account/agent/ios/download.do?version=1.04)

**增加功能：**

1. 
iOS SDK Crash 报告；
1. 
Xcode 自动上传符号表错误修正

## OneAPM iOS SDK 1.0.4



发布日期：2015/1/13

下载链接：[iOS SDK 1.0.4](https://user.oneapm.com/account/agent/ios/download.do?version=1.04)

**修复问题：**
1. 
增加1.0.3遗漏的 x86-64 支持；
1. 
修正使用某些社交分享组件时导致崩溃的问题。

**增加功能：**

1. 
终端移动无线接入网络制式识别；
1. 
新增 iPhone6/Plus 支持。

## OneAPM iOS SDK 1.0.3



发布日期：2014/8/29

**修复问题：**

1. 
解决了在某些情况下，监测 UI 时产生异常的 bug。

**增加功能：**

增加了控制 SDK log 的接口，log 默认不输出打印。

## OneAPM iOS SDK 1.0.2

发布日期：2014/8/29

**修复问题：**

解决了某些情况下记录 HTTP 产生异常的 bug。
**增加功能：**
1. 
增加对 ARM 64 架构 CPU 的支持；
1. 
增加对 UI, JSON, CoreData, Image 的测量。

**特别说明：**

编译时在"Build Settings"中，为"Other Linker Flags"增加"-all_load" 选项。

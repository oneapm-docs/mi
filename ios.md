#OneAPM iOS SDK Release Note
-------------

##2016-03-16 V2.2.0.8

* 增加JSError功能，展示错误信息 ，以及相关堆栈信息；
* 支持监控Ajax请求性能状况；
* 优化交互功能，增加慢交互详情功能；
* 显示慢交互方法调用层级，执行时间，cpu及内存占有率等；
* 优化在个别系统版本下崩溃后数据上报卡顿，优化崩溃轨迹的展示流程；
* 优化启动时间


##2016-02-28 V2.1.3 


* WebView代码逻辑的优化 

* 修复了一些小bug




##2016-01-27 V2.1.2 

1.Bitcode打包改进

2.修正探针导致APP旋转开关为打开状态


## 2016-01-15 V2.1.1

**特点：**

* 交互数据（慢交互除外）：

 总览中展示View Loading，UIImage，DataBase，Json，NetWork,  WebView六种数据的执行时间等信息；
     
 交互列表中展示页面（ViewController）的具体交互数据信息。
 
* WebView ：
  
  请求网络url性能相关信息(暂不支持JS Errors)；
    慢加载资源耗时信息（目前有link、img、css、script几种类型，暂不支持ajax）。
    
* 崩溃轨迹:
  
  崩溃发生前的交互行为路径信息，最大支持到19条；

## OneAPM iOS smart SDK 2.0.0

**特点**：完全重构版，重写了90%代码。

 * 识别设备类型（iPhone/iPad/iPod、操作系统版本、运营商类型）；

* 统计 http 访问情况、出错情况。

* 修复与百度地图、极光推送等第三方 SDK 不兼容问题；

* 修复当路由被劫持，访问 ip.taobao 连接成功，但返回数据不合法时，数据无法上报的问题；

* 修复首次安装时重试间隔时间错误。

* SDK 自身日志系统改善，统一输出格式，使用[OneAPM printLog:YES］开启或关闭，默认为关闭状态。



##2015-8-27 V1.1.3

* 支持监控通过 NSURLSession 发送的 HTTP 请求；
 
* 增加用户自定义信息功能；
 
* 性能优化；

* 解决 Agent 初始化工程中可能发送 crash 的问题。

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
##2015-08-04 V1.1.2


* 增加对 SDWebImage 的 HTTP 请求监控；

* 其它优化。

* 解决使用 ASIHttpRequest 时偶发崩溃的问题；

* 解决工程名字为中文时捕获的 crash log 包含乱码的问题；

## 2015-06-09 V1.1.1

* 修改在一些场景中统计的 http 请求不完善的问题。

## 2015-06-03 V1.1.0


* iOS SDK Crash 报告；

* Xcode 自动上传符号表错误修正

## 2015-01-13 V1.0.4

* 增加1.0.3遗漏的 x86-64 支持；

* 修正使用某些社交分享组件时导致崩溃的问题。

* 新增终端移动无线接入网络制式识别；

* 新增 iPhone6/Plus 支持。

## 2014-08-29 V1.0.3

* 解决了在某些情况下，监测 UI 时产生异常的 bug。

* 增加了控制 SDK log 的接口，log 默认不输出打印。

## 2014-08-29 V1.0.2

* 解决了某些情况下记录 HTTP 产生异常的 bug。

* 增加对 ARM 64 架构 CPU 的支持；
 
* 增加对 UI, JSON, CoreData, Image 的测量。

**特别说明：**

编译时在"Build Settings"中，为"Other Linker Flags"增加"-all_load" 选项。

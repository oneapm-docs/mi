# 升级Android Agent 2.0.4后嵌入Token那行代码报错？

* 1、版本信息：

（1）探针类型：Android SDK

（2）探针版本：2.0.4

（3）操作系统版本：无

（4）开发工具：无

（5）JRE：jre1.8.60

（6）JDK：jdk1.8.60

（7）JVM：Java HotSpot(TM) 64-Bit Server VM

* 2、问题回复：

Android Agent 2.0.4 更新后的启动方式与之前版本略有不同，需要修改为：

（1）在默认启动的 Activity 中 import OneApmAgent类。

```java
import com.oneapm.agent.android.OneApmAgent;
```

（2）        在 onCreate() 方法中加入如下：

```java
OneApmAgent.init(this).setToken("--Your Token--").start();
```

如图：

（3）Clean Project，并重新启动应用程序。

运行嵌码完成后的APK，连接电脑使用LogCat过滤TAG = oneapm查看log日志。

若出现 "oneapm is running normally version: OneAPM-Version" 的 log 则表示嵌码成功。

 
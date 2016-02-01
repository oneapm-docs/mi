# 2.0.4. 以上版本安装方式

获取探针的方式请根据自身环境并参照2.0.3.* 版本，启动及配置如下；

# 1、启动Agent

在待监测App的入口Activity （Main Activity）源文件中导入OneApmAgent类

```java
import com.oneapm.agent.android.OneApmAgent;
```

在 onCreate() 方法中加入如下方法来初始化OneAPM（其中包含了根据应用程序名称而生成的授权编号）

```java
OneApmAgent.init(this)
.setToken("<use app token created at step 1>")
.start();
```

配置渠道信息，在AndroidManifest.xml文件中添加meta-data项，要添加在Application标签内部

```xml
<meta-data android:name = "BluewareChannel" android:value="***" />
```

***代表App的发布渠道，如下图所示:

![agent](agent.png)

# 2、加统计分析功能

在每个 Activity 中导入 OneApmAnalysis 类

```java
import com.oneapm.agent.android.module.analysis.OneApmAnalysis;
```

在每个 Activity 的 onPause() 方法中添加代码:

```java
OneApmAnalysis.onPause();
```

如下图所示：

![](eclipse-statistics-onpause.png)

在每个 Activity 的 onResume() 方法中添加代码:

```java
OneApmAnalysis.onResume();
```

如下图所示：

![](eclipse-statistics-onresume.png)

**注意**：如果两个Activity是继承关系，只需要在父Activity添加即可，如果在两个Activity中同时添加，则会造成重复统计。
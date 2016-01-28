# 2.0.4.*以上版本安装方式

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



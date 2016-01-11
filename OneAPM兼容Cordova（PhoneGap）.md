# OneAPM兼容Cordova（PhoneGap）

**兼容Cordova**

如果想对Cordova监控就需要在用到Cordova的Activity中获取Cordova的webView对象，然后调用如下方法即可

```java
BlueWare.compatibleCordova(webView);
```

Cordova 5.0和以后的版本 使用如下代码获取WebView

```java
WebView wV = (WebView)appView.getEngine().getView();
```

小于5.0版本的，在Activity中应该可以直接获取。

*资料下载*


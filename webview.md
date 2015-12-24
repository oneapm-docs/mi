# WebView


WebView 界面用于监控移动应用中 WebView 页及WebView中的请求的性能状况，包含其加载时间、执行时间、执行次数、JS错误等。

![](http://i.imgur.com/RFXMT5q.png)

如图，左侧列表按照 WebView 所在的 Activity 进行归类，从平均执行时间、总执行时间、执行次数三个角度进行展示。
右侧则展示 WebView 平均执行时间、执行次数的实时动态图。在下部，有 WebView 慢加载追踪列表，展示了慢 Webview 的白屏时间、总耗时、发生时间、操作系统及版本。
其中，白屏时间采取了精确的算法，旨在衡量用户真实体验到的加载状况。

![](http://i.imgur.com/JX49Bsl.png)

点击任一慢加载 WebView 名，进入其详情页。该页面以时序图的形式展示了单条 WebView 的详细信息。时序图基于 HTML5 页面加载解析过程创建，您可以清晰地了解页面渲染时各个流程的耗时情况，从而有针对地优化代码。提供资源加载时序图，有效判别造成页面加载慢的耗时资源。

![](http://i.imgur.com/vxFhqDf.png)

关键词：*WebView JS 资源加载 Ajax JS错误 H5*
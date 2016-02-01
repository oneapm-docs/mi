# ANR 数据抓取及展示



ANR，全称 Application Not Responding 或 The Application of Non Response，意思是“应用无响应”。本文主要介绍 ANR 产生原因以及 OneAPM Moblie Insight 提供的 ANR 数据抓取及展示功能。
引起 ANR 问题的根本原因，可以大致归为两类：

* 应用进程自身引起
例如：主线程阻塞、挂起、死循环。应用进程的其他线程 CPU 占用率过高，导致主线程无法抢占 CPU 时间片等。

* 其他进程间接引起
例如：当前应用进程与其他进程开展通信请求，其他进程长时间没有反馈。或者其他进程 CPU 占用率过高，导致当前应用进程无法抢占 CPU 时间片。

ANR 对于应用的影响并不亚于 Crash。那我们如何监控 ANR 呢？
OneAPM Mobile Insight 提供了 ANR 监控功能：
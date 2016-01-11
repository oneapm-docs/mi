# Mac OS下 Android Studio 如何卸载探针？

很多人问在  Mac OS下 Android Studio 如何卸载探针？

因为Android Studio 为了提高编译的速度，加入了 daemon 的缓存机制，这个缓存可能是由于 bug，经常无法清理干净。为此，解决问题的方法也是手动去清理一下缓存。

* 1、Mac 环境的缓存路径是：

/Users/用户名/.gradle/daemon/2.4.*/daemon

cd 进去删除 registry.bin 和 registry.bin.lock 两个文件即可。

* 2、Windows下面相比较为简单

例如： C:\Users\andy\.gradle\daemon\2.0\daemon下面的，同样也删除以上两个文件即可。

 

附：版本信息：

（1）探针类型：Android SDK

（2）探针版本：2.0.*

（3）操作系统版本：Mac OS

（4）开发工具：Android Studio 1.3.*

（5）JRE：jre1.8

（6）JDK：jdk1.8

（7）JVM：Java HotSpot(TM) 64-Bit Server VM
# Mac OS下 Android Studio 如何卸载探针？

很多人问在  Mac OS下 Android Studio 如何卸载探针？

因为Android Studio 为了提高编译的速度，加入了 daemon 的缓存机制，这个缓存可能是由于 bug，经常无法清理干净。为此，解决问题的方法也是手动去清理一下缓存。

* 1、Mac 环境的缓存路径是：/Users/用户名/.gradle/daemon/2.4【版本号】/daemon
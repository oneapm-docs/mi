# SDWebImage 造成的 crash 问题


## 故障说明

SDWebImage 是一个项目开发中必不可少的三方库，但是当与 OneAPM 的 SDK 结合开发项目时，若 SDWebImage 的版本不是最新的，会出现 crash 情况，在 ios7 系统 iphone4 设备下的频率尤其高，crash log 打印如下图：
![](1Z.jpg)


## 解决办法

此时建议用户去 GitHub 下载最新的 SDWebImage 库，https://github.com/rs/SDWebImage。




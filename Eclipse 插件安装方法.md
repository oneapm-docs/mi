# Eclipse 插件安装方法

## 1. 安装 SDK

OneAPM Android SDK支持在 Eclipse 集成开发环境中直接使用和部署。


### **1. 查看 Eclipse 版本号**



OneAPM Eclipse 插件支持 Eclipse 3.8 及以上版本，请于安装前确认您使用的 Eclipse 版本号：

Mac OS 下
         点击进入“关于 Eclipse”
Windows 下
         点击进入“About Eclipse”或者是“About ADT”
         
(1)点击Help, 打开 “关于 Eclipse” 可查看当前版本号

   ![](A119.jpg)
   

(2)如下图所示, 红色方框内的版本号信息.(如未见详细版本号,可点击进人“Eclipse Plugin”查看,详见步骤(3)。)
![](A120.jpg)

(3)如果您的eclipse版本号在上图中没有出现, 可以点击上图中的底部 Eclipse 图标,点击后弹出对话框, 如下图所示:

![](A121.jpg)


### **2.安装 OneAPM Eclipse 插件**

（1）在 Eclipse 集成开发环境中点击“Help”菜单，选择“Install New Software...”

![](A122.jpg)
（2）点击Work with项右侧的“Add…”按钮来增加 OneAPM Eclipse 插件.
![](A123.jpg)

（3）设置插件的名称（比如OneAPM）以及URL地址:
 Eclipse 插件需要 JAVA_HOME 环境变量，目前已支持最新 4.4 版本 Eclipse。
 Eclipse 4.4 及之后版本请使用以下链接：   
      
     ``` 
     https://download.oneapm.com/android_agent/eclipse_gt_4.4/
     ```

注：OneAPM Eclipse 4.4 插件需要 JDK 1.8。
 
 Eclipse 4.4 之前版本请使用以下链接：
 
     ```
     https://download.oneapm.com/android_agent/eclipse_lt_4.4/
     ```
 
 例如, Eclipse 4.4版本就可使用
 ```
 https://download.oneapm.com/android_agent/eclipse_gt_4.4/
 ```
![](A124.jpg)
在Work with选项中选中刚才添加的资料库，在下方列表中点击“Select All”选中所有的插件。点击“Next >”到下一步。
![](A125.jpg)
查看插件描述并点击“Next >”进入下一步。
![](A126.jpg)
查看许可协议，选择“I accept the terms of the license agreement”，点击“Finish>”进入下一步。
![](A127.jpg)

选择信任插件的签名证书，点击“OK”。
![](A128.jpg)
点击“Yes”重启 Eclipse 来完成插件的安装。
![](A129.jpg)
插件安装完成后，右击需要监控的App，选择“安装OneAPM”
![](A130.jpg)

Eclipse 会自动添加“oneapm-android-agent.jar”包到libs目录下，若没有libs目录请新建一个。

![](A131.jpg)

注：Eclipse 插件目前只支持JDK（1.5 - 1.8）运行环境（不支持只有JRE的运行环境）
Window 安装Eclipse插件时，请在没有空格和特殊字符的路径安装JDK
Eclipse 插件需要使用JAVA_HOME环境变量，请检查环境变量,如果提示SDK 安装后提示错误信息：
由于使用 JRE 运行 Eclipse 导致 OneAPM 无法正确加载，请参考链接： 

```
https://oneapm.kf5.com/posts/view/48050/
```


静候 5 分钟后，若无应用程序相关性能数据展现，或安装过程中出现问题：请联系 OneAPM 客服人员：

* 技术咨询热线： 400-622-3101

* 销售咨询热线： 400-659-1230

* OneAPM客服邮箱：support@oneapm.com

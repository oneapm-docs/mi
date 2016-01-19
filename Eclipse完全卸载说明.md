# Eclipse完全卸载说明

**注意**：Eclipse 安装 Android Agent 2.0.3.\* 版本升级到2.0.4.\*  需要先卸载旧探针再进行安装。

首先在 Eclipse 中卸载 OneAPM 的 Agent 插件： Help -> About ADT -> Installation Details。

![eclipse](eclipse1.png)

![eclipse](eclipse2.png)

![eclipse](eclipse3.png)

![eclipse](eclipse4.png)

打开Eclipse的安装目录：**\eclipse\plugins**

删除下面的目录：

![eclipse](eclipse5.png)

**\eclipse\features**

删除下面的目录：

![eclipse](eclipse6.png)

编辑 artifacts.xml 文件：

![eclipse](eclipse7.png)

搜索“oneapm”关键字，删除所有包含“oneapm”的artifact节点元素。

![eclipse](eclipse8.png)

重启Eclipse即可。
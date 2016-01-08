# Maven 插件安装方法

最新 Maven 插件版本号为2.0.3,以下称为 PLUGIN_VERSION。

* 1、下载 Maven 插件包解压，假设解压之后的路径是PATH_TO_ONEAPM_MAVEN_PATH 后续会用到；解压之后会有3个.jar文件一个 .pom 文件，这些文件下面的操作步骤会用到。

* 2、注册 Agent 和 plugin 下的 jar 包为本地 Maven 库

**注册 oneapm-android-agent.jar**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=agent.android -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH/oneapm-android-agent.jar`

**注册 class.rewriter.jar**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=class.rewriter -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH/class.rewriter.jar`

**注册 oneapm-android-maven-plugin.jar和plugin.maven.pom**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=plugin.maven -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH\plugin.maven.jar -DpomFile=PATH_TO_ONEAPM_MAVEN_PATH\plugin.maven.pom`


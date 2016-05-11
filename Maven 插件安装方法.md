# Maven 插件安装方法

## 1.命名你的应用程序

 点击进入OneAPM Mobile Insight[集成安装界面](https://mi.oneapm.com/mobile/app/setup#/)，命名应用程序。

## 2. [下载并解压 OneAPM SDK](https://user.oneapm.com/account/agent/gradle/download.do?version=latest)


最新 Maven 插件版本号为2.0.3,以下称为 PLUGIN_VERSION。

* 1、下载 Maven 插件包解压，假设解压之后的路径是PATH_TO_ONEAPM_MAVEN_PATH 后续会用到；解压之后会有3个.jar文件一个 .pom 文件，这些文件下面的操作步骤会用到。

* 2、注册 Agent 和 plugin 下的 jar 包为本地 Maven 库

**注册 oneapm-android-agent.jar**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=agent.android -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH/oneapm-android-agent.jar`

**注册 class.rewriter.jar**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=class.rewriter -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH/class.rewriter.jar`

**注册 oneapm-android-maven-plugin.jar和plugin.maven.pom**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=plugin.maven -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=PATH_TO_ONEAPM_MAVEN_PATH\plugin.maven.jar -DpomFile=PATH_TO_ONEAPM_MAVEN_PATH\plugin.maven.pom`

**例如，配置一个例子：**

`mvn install:install-file -DgroupId=com.oneapm.agent.android -DartifactId=plugin.maven -Dversion=PLUGIN_VERSION -Dpackaging=jar -Dfile=E:\agent\gitlab\android-maven-plugin\target\plugin.maven.jar -DpomFile=E:\agent\gitlab\android-maven-plugin\target\plugin.maven.pom`

**注意：-Dfile=这个后面一定不要有空格，否则运行 Maven 会报错！！！**

* 3、配置本地 pom.xml 文件，添加刚才注册的 jar 包，如下 

依赖：

```xml
<dependency>
    <groupId>com.oneapm.agent.android</groupId>
    <artifactId>agent.android</artifactId>
    <version>1.0.8</version>
</dependency>
```

插件：

```xml
<plugin>
    <groupId>com.oneapm.agent.android</groupId>
    <artifactId>plugin.maven</artifactId>
    <version>1.0.8</version>
    <executions>
        <execution>
            <goals>
                <goal>instrument</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

完整如下: 

```xml
<groupId>xxx.yyy.zzzz</groupId>
<artifactId>TestMavenAndroid02</artifactId>
<version>1.0</version>
<packaging>apk</packaging>
<dependencies>
    <dependency>
        <groupId>com.google.android</groupId>
        <artifactId>android</artifactId>
        <version>4.1.1.4</version>
        <scope>provided</scope>
    </dependency>
    <dependency>
        <groupId>com.oneapm.agent.android</groupId>
        <artifactId>agent.android</artifactId>
        <version>1.0.8</version>
    </dependency>
</dependencies>
<build>
    <finalName>${project.artifactId}</finalName>
    <sourceDirectory>src</sourceDirectory>
    <plugins>
        <plugin>
            <groupId>com.jayway.maven.plugins.android.generation2</groupId>
            <artifactId>android-maven-plugin</artifactId>
            <version>4.0.0-rc.2</version>
            <configuration>
                <sdk>
                    <platform>19</platform>
                </sdk>
                <manifest>
                    <debuggable>true</debuggable>
                </manifest>
            </configuration>
            <extensions>true</extensions>
        </plugin>
        <plugin>
            <groupId>com.oneapm.agent.android</groupId>
            <artifactId>plugin.maven</artifactId>
            <version>1.0.8</version>
            <executions>
                <execution> 
                    <goals>
                        <goal>instrument</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins> 
</build>
```

* 4、配置授权信息

确保应用程序的 AndroidManifest.xml 配置文件中，引入了 INTERNET 和 ACCESS_NETWORK_STATE 三个请求授权:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
```

若想使用 Crash 快照功能，请引入以下授权信息

```xml
<uses-permission android:name="android.permission.GET_TASKS" />
```

如果使用基站定位，请添加如下权限：

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

注意：如果您的应用使用 progurd 混淆，请配置以下

```
-dontwarn org.apache.commons.**
-keep class org.apache.http.impl.client.**
-dontwarn org.apache.commons.**
-keep class com.blueware.** { *; }
-dontwarn com.blueware.**
-keepattributes Exceptions, Signature, InnerClasses
```

注意：如果您希望保留行号信息，建议您在 proguard.cfg 中添加如下代码：

```
- keepattributes SourceFile ,LineNumberTable
```

* 5、启动 Agent

在默认 Activity 中 import BlueWare 类：

```java
import com.blueware.agent.android.BlueWare;
```

在 onCreate() 方法中加入如下 call 来初始化 oneAPM（其中包含了在步骤 2 中根据应用程序名称而生成的授权编号）：

```java
BlueWare.withApplicationToken(
"<use app token created at step 1>")
.start(this.getApplication());
```

* 6、静候 5 分钟，开启 OneAPM 之旅





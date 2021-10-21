> 当前演示环境为虚拟机中的Windows系统，Mac及Linux、Ubuntu等请自行寻找安装教程

## JDK下载

> oracle官方下载地址需要登录，所以这里选择去华为镜像仓库去下载，版本更具个人喜好选择下载，我这下载JDK8
>
> 地址：[https://repo.huaweicloud.com/java/jdk/](https://repo.huaweicloud.com/java/jdk/)

![image-20211013133939633](安装JDK/image-20211013133939633.png)

> 根据自身系统版本下载对应的安装程序

![image-20211013134059998](安装JDK/image-20211013134059998.png)

## 执行安装

> 一直下一步就可以，中间的安装位置可以自定义但要记录下，后面配置系统环境变量要用到

![image-20210926143255373](安装JDK/image-20210926143255373.png)

> JDK8还会有个弹窗是安装JRE的，非JDK8忽略这一步。这里不需要安装，应为JDK中集成有JRE

![image-20210926145652338](安装JDK/image-20210926145652338.png)

> 安装完成

![image-20210926144153916](安装JDK/image-20210926144153916.png)

## 配置环境变量

> 现在虽然已经安装完了，但是没有配置全局变量，Java命令还是不能用

> 打开资源管理器 => 单击此电脑 => 右键选属性 => 关于中找到高级系统设置 => 点击环境变量

![image-20210926144837803](安装JDK/image-20210926144837803.png)

> 系统环境变量中新增 **JAVA_HOME** 、**CLASSP_PATH** ，**PATH** 中追加一条记录并置顶

>新增 *JAVA_HOME* ：**填刚才的安装路径**
>
>新增 *CLASS_PATH* ：`.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`
>
>编辑 *PATH* 追加：`%JAVA_HOME%\bin`

![image-20210926173303865](安装JDK/image-20210926173303865.png)

> 确定保存

![image-20210926173610126](安装JDK/image-20210926173610126.png)

> 打开CMD命令行，执行 `java -version` 与 `javac`

![image-20211013134642855](安装JDK/image-20211013134642855.png)

> **重点！！！！！！！！！！！！！** CMD不能正常使用，需要使用支持Linux命令的控制台 例：`git bash`

## SSH远程连接命令

```shell
#ssh 用户名@服务器IP
ssh root@124.70.28.3
```



## SCP传输命令

### 上传

> 还有就是上传的路径是否有权限被访问，如root权限可访问所有位置

#### 单文件上传至服务器

> 前面一个参数为当前系统中的文件位置，后一个参数为要上传服务器的信息及要上传的文件夹或重命名上传

```shell
# scp filePath/fileName username@ip:/filePath[/fileName]
scp ./test.jar root@124.70.28.3:/app
scp ./test.jar root@124.70.28.3:/app/test1.jar
```

#### 文件夹上传至服务器

> 前面一个参数为当前系统中的文件夹位置，后一个参数为要上传服务器的信息及要上传的文件夹

```shell
# scp -r filePath username@ip:/filePath
scp -r ./log root@124.70.28.3:/log
```

### 下载

> 以下为下载，原理与上传相似，知识参数换了个位置罢了

#### 从服务器下载单个文件

```shell
# scp username@ip:/filePath/fileName filePath/fileName
scp root@124.70.28.3:/app/test1.jar ./test.jar
```

#### 从服务器下载文件夹

```shell
# scp -r username@ip:/filePath filePath
scp -r root@124.70.28.3:/log ./log
```

## 基于DockerDesktopForWindows安装

> Docker Desktop for Windows 的设置页面有开启k8s的地方，但是不能直接使用

> 参考该链接：[https://github.com/AliyunContainerService/k8s-for-docker-desktop/tree/v1.22.4](https://github.com/AliyunContainerService/k8s-for-docker-desktop/tree/v1.22.4)

> 其中执行安装脚本时会频繁出现Error拉去镜像失败，多重复执行几次直到没有Error

### 关于部署Kubernetes-dashboard报错

> 这里需要注意两个域名，因为这两个域名无法正常方法问，需要在本地hosts文件配置

- **raw.githubusercontent.com：** 这个是拉去Github资源
- **kubernetes.docker.internal：** 这个不知道干嘛的，设置成 `127.0.0.1` 即可

> `raw.githubusercontent.com` 可以通过 [IP查询链接](https://www.ipaddress.com/) 查询最新的IP指向

> hosts示例
```shell
185.199.108.133 raw.githubusercontent.com
127.0.0.1 kubernetes.docker.internal
```
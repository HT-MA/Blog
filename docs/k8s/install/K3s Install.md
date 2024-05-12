
K3s 是一个轻量级的 Kubernetes 发行版，旨在简化 Kubernetes 的部署和管理。它由 Rancher Labs 开发，专注于在资源受限的环境中（如边缘计算、IoT 设备、测试/开发环境等）提供轻量级的 Kubernetes 解决方案。

K3s 的设计目标包括：

1. **轻量级：** K3s 采用了更轻量的架构和组件，去除了一些不常用的功能和依赖，使得它的二进制文件大小只有几十兆，内存占用更少，适合于资源受限的环境。

2. **简化部署：** K3s 提供了一个简单的安装脚本，可以快速地在单个节点或多个节点上部署 Kubernetes 集群。安装过程中，它会自动完成证书生成、配置文件的创建、组件的部署等操作，无需复杂的手动配置。

3. **自动化运维：** K3s 集成了一些自动化运维功能，如自动修复、自动升级等，使得 Kubernetes 集群的管理更加简单和高效。

4. **高度兼容性：** K3s 兼容标准的 Kubernetes API 和组件，可以与标准的 Kubernetes 工具和生态系统无缝集成，可以运行大部分基于 Kubernetes 的应用程序。

5. **安全性：** 尽管 K3s 简化了 Kubernetes 的部署和管理，但它仍然注重安全性。K3s 支持 TLS 加密通信、RBAC 权限控制、安全的默认设置等安全功能。

总的来说，K3s 是一个针对边缘计算和资源受限环境设计的轻量级 Kubernetes 发行版，它简化了 Kubernetes 的部署和管理过程，同时保持了 Kubernetes 的核心功能和兼容性。因此，它受到了在边缘计算、IoT、测试/开发等场景下的广泛关注和应用。
## ***`Install`***


- update

```shell
yum upodate -y
```

- install tools

```shell
yum install -y vim net-tools wget
```

- set hostname

```shell
hostnamectl set-hostname master
hostnamectl set-hostname node01
hostnamectl set-hostname node02
```

- set static network

```shell
[root@matser ~]# cat /etc/sysconfig/network-scripts/ifcfg-ens33
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=ens33
UUID=edc3484d-b159-497e-a29b-b0a625d26418
DEVICE=ens33
ONBOOT=yes
IPADDR=192.168.43.135
NETMASK=255.255.255.0
GATEWAY=192.168.43.2
DNS1=114.114.114.114
DNS2=8.8.8.8
```



## ***`Install k3s`***

- master

```shell
curl -sfL https://rancher-mirror.rancher.cn/k3s/k3s-install.sh \
INSTALL_K3S_MIRROR=cnINSTALL_K3S_VERSION=v1.26.4+k3s1 sh -s - \
--with-node-id --bind-address 0.0.0.0
```

- node
## Ubuntu
在 Ubuntu 20.04 上安装 Docker 可以通过官方的 Docker 脚本来完成。以下是安装 Docker 的步骤：

1. **更新包管理器**：

```bash
sudo apt update
```

2. **安装依赖包，以允许 apt 通过 HTTPS 使用存储库**：

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

3. **添加 Docker 的官方 GPG 密钥**：

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

4. **添加 Docker 的稳定存储库**：

```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

5. **更新 apt 包索引**：

```bash
sudo apt update
```

6. **确保从 Docker 而不是默认 Ubuntu 存储库安装**：

```bash
apt-cache policy docker-ce
```

7. **安装 Docker**：

```bash
sudo apt install docker-ce
```

8. **启动 Docker 服务**：

```bash
sudo systemctl start docker
```

9. **验证 Docker 是否正确安装**：

```bash
sudo docker --version
```

这些步骤应该能够在 Ubuntu 20.04 上成功安装 Docker。如果你使用的是非 root 用户，记得将该用户添加到 `docker` 用户组中，这样它就可以执行 Docker 命令而无需使用 `sudo`。



## Centos install docker use ansible
- **install docker playbook**

```yaml
---
- name: Install Docker
  hosts: all
  become: true
  tasks:
    - name: Install required packages
      yum:
        name:
          - yum-utils
          - device-mapper-persistent-data
          - lvm2
        state: present

    - name: Add Docker repository
      yum_repository:
        name: docker-ce-stable
        description: Docker CE Stable - $basearch
        baseurl: https://download.docker.com/linux/centos/7/x86_64/stable
        gpgcheck: yes
        gpgkey: https://download.docker.com/linux/centos/gpg
        enabled: yes

    - name: Install Docker
      yum:
        name: docker-ce
        state: present

    - name: Start Docker service
      service:
        name: docker
        state: started
        enabled: yes
```

- **confirm docker version**

```yaml
- name: Execute Docker version command
  hosts: all  # 你的目标主机
  tasks:
    - name: Run Docker version command
      become: true  # 使用管理员权限
      command: docker version
      register: docker_version_output  # 将命令输出保存到变量中

    - name: Display Docker version output
      debug:
        var: docker_version_output.stdout_lines  # 显示命令输出

```


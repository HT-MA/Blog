当使用 Ansible 进行自动化时，可以使用各种模块执行不同的任务。以下是几个常用的 Ansible 模块：

**1. apt/yum：** 这些模块用于在基于 Debian/Ubuntu 或基于 Red Hat/CentOS 的系统上安装、升级或删除软件包。例如，`apt` 模块可用于在 Ubuntu 上安装软件包，而 `yum` 模块则适用于在 CentOS 上进行相同的操作。

```yaml
- name: Install Apache on Ubuntu
  apt:
    name: apache2
    state: present

- name: Install Apache on CentOS
  yum:
    name: httpd
    state: present
```

**2. copy/template：** 这些模块用于在远程主机上复制文件或将模板文件传输到远程主机。`copy` 模块用于复制本地文件，而 `template` 模块用于将 Jinja2 模板渲染为文件。

```yaml
- name: Copy file to remote host
  copy:
    src: /path/to/local/file
    dest: /path/to/remote/file

- name: Deploy template file to remote host
  template:
    src: /path/to/local/template.j2
    dest: /path/to/remote/file
```

**3. service/systemd：** 这些模块用于管理系统服务。`service` 模块适用于传统的 SysVinit 系统，而 `systemd` 模块则用于管理 systemd 服务。

```yaml
- name: Start Apache service
  service:
    name: apache2
    state: started

- name: Restart nginx service using systemd
  systemd:
    name: nginx
    state: restarted
```

**4. command/shell：** 这些模块用于在远程主机上执行命令或脚本。`command` 模块用于执行简单的命令，而 `shell` 模块用于执行复杂的命令、管道或 shell 脚本。

```yaml
- name: Run a simple command
  command: ls /path/to/directory

- name: Run a shell script
  shell: /path/to/script.sh
```

**5. `file`：** 这个模块用于管理远程主机上的文件和目录。可以创建、删除、修改文件和目录的权限、所有者和组。

```yaml
- name: Create a directory
  file:
    path: /path/to/directory
    state: directory

- name: Set permissions on a file
  file:
    path: /path/to/file
    mode: 0644
```

这些只是 Ansible 模块中的一小部分。Ansible 提供了大量的模块，涵盖了系统管理、网络管理、云资源管理等各个方面，可以根据需要选择合适的模块来完成任务。

<span style="color: red;">这是红色字体</span>

<span style="color: blue;">这是红色字体</span>

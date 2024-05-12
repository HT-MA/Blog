以下是一些常用的 Docker 命令：

1. **镜像操作：**
   - `docker images`：列出本地所有的镜像。
   - `docker pull <image_name>`：从 Docker Hub 下载指定的镜像。
   - `docker rmi <image_id>`：删除本地的镜像。
   - `docker build -t <image_name> <Dockerfile_path>`：根据 Dockerfile 构建镜像。

2. **容器操作：**
   - `docker ps`：列出当前正在运行的容器。
   - `docker ps -a`：列出所有的容器，包括已停止的。
   - `docker run <image_name>`：从指定的镜像创建并运行一个容器。
   - `docker start <container_id>`：启动一个停止的容器。
   - `docker stop <container_id>`：停止一个运行中的容器。
   - `docker rm <container_id>`：删除一个容器。

3. **容器日志和状态：**
   - `docker logs <container_id>`：查看容器的日志。
   - `docker inspect <container_id>`：获取容器的详细信息，包括 IP 地址、端口映射等。

4. **容器交互：**
   - `docker exec -it <container_id> /bin/bash`：在运行中的容器中启动一个交互式的 Bash shell。
   - `docker attach <container_id>`：连接到正在运行的容器的标准输入、输出和错误流。

5. **网络操作：**
   - `docker network ls`：列出 Docker 网络。
   - `docker network inspect <network_id>`：查看特定 Docker 网络的详细信息。
   - `docker network create <network_name>`：创建一个自定义 Docker 网络。

6. **数据卷操作：**
   - `docker volume ls`：列出 Docker 数据卷。
   - `docker volume create <volume_name>`：创建一个 Docker 数据卷。
   - `docker volume inspect <volume_name>`：查看 Docker 数据卷的详细信息。

这些命令只是 Docker 提供的一小部分功能，但它们涵盖了常见的使用场景，可以让你开始使用 Docker 进行容器化应用程序的管理和操作。
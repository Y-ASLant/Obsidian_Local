# Debian 官方安装脚本
```sh
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

# CentOS 安装脚本

> [!BUG] 软件源使用阿里云

```sh
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

# Hello World
Docker 允许在容器内运行应用程序，使用 docker run 命令来在容器内运行一个应用程序。

```sh
ASLant@Ubuntu :~$ docker run ubuntu: 15.10 /bin/echo "Hello world"
```

输出结果：
```sh
Hello world
```

> [!BUG] 各个参数解析：

Docker: Docker 的二进制执行文件。

Run: 与前面的 docker 组合来运行一个容器。

Ubuntu: 15.10 指定要运行的镜像，Docker 首先从本地主机上查找镜像是否存在，如果不存在，Docker 就会从镜像仓库 Docker Hub 下载公共镜像。

/bin/echo "Hello world": 在启动的容器里执行的命令

以上命令完整的意思可以解释为：Docker 以 ubuntu 15.10 镜像创建一个新容器，然后在容器里执行 bin/echo "Hello world"，然后输出结果。




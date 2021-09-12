- [安装`docker-compose`](#安装docker-compose)
  - [运行此命令下载`docker-compose`的当前稳定版本](#运行此命令下载docker-compose的当前稳定版本)
  - [对`docker-compose`文件应用可执行权限](#对docker-compose文件应用可执行权限)
  - [创建`docker-compose`软链接到`/usr/bin`下，以供`sudo`使用](#创建docker-compose软链接到usrbin下以供sudo使用)
  - [查看`docker-compose`版本](#查看docker-compose版本)

# 安装`docker-compose`

## 运行此命令下载`docker-compose`的当前稳定版本

```shell
[qiqi@node01 ~]$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

## 对`docker-compose`文件应用可执行权限

```shell
[qiqi@node01 ~]$ sudo chmod +x /usr/local/bin/docker-compose
```

## 创建`docker-compose`软链接到`/usr/bin`下，以供`sudo`使用

```shell
[qiqi@node01 ~]$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

## 查看`docker-compose`版本

```shell
[qiqi@node01 ~]$ docker-compose --version
```


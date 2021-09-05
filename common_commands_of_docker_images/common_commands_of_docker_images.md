- [`docker`镜像常用命令](#docker镜像常用命令)
  - [查看本地镜像列表](#查看本地镜像列表)
  - [查看`docker`服务信息](#查看docker服务信息)
  - [查看`docker`帮助信息](#查看docker帮助信息)
  - [查看`docker`命令帮助信息](#查看docker命令帮助信息)
  - [下载镜像](#下载镜像)
  - [根据`TAG`下载镜像](#根据tag下载镜像)
  - [根据`DIGEST`下载镜像](#根据digest下载镜像)
  - [搜索镜像](#搜索镜像)
  - [根据`TAG`删除镜像](#根据tag删除镜像)
  - [根据`IMAGE ID`删除镜像](#根据image-id删除镜像)
  - [强制删除镜像](#强制删除镜像)
  - [根据`IMAGE ID`删除所有镜像](#根据image-id删除所有镜像)
  - [根据`IMAGE ID`强制删除所有镜像](#根据image-id强制删除所有镜像)
  - [保存镜像到本地](#保存镜像到本地)
  - [从本地加载镜像到本地镜像仓库](#从本地加载镜像到本地镜像仓库)

# `docker`镜像常用命令

## 查看本地镜像列表

```shell
[qiqi@node01 ~]$ sudo docker images
```

## 查看`docker`服务信息

```shell
[qiqi@node01 ~]$ sudo docker info
```

## 查看`docker`帮助信息

```shell
[qiqi@node01 ~]$ sudo docker --help
```

## 查看`docker`命令帮助信息

```shell
[qiqi@node01 ~]$ sudo docker images --help
```

## 下载镜像

```shell
[qiqi@node01 ~]$ sudo docker pull hello-world
```

## 根据`TAG`下载镜像

```shell
[qiqi@node01 ~]$ sudo docker pull hello-world:latest
```

## 根据`DIGEST`下载镜像

```shell
[qiqi@node01 ~]$ sudo docker pull redis:DIGEST@sha256:18c2f1d8bd5f93d38474175891eabda41aa476951ceb22e97db78ff5d8c197bd
```

## 搜索镜像

```shell
[qiqi@node01 ~]$ sudo docker search hello-world
```

## 根据`TAG`删除镜像

```shell
[qiqi@node01 ~]$ sudo docker image rm nginx:latest
[qiqi@node01 ~]$ sudo docker rmi nginx:latest
```

## 根据`IMAGE ID`删除镜像

```shell
[qiqi@node01 ~]$ sudo docker image rm 02c7f2054405
[qiqi@node01 ~]$ sudo docker rmi 02c7f2054405
```

## 强制删除镜像

```shell
[qiqi@node01 ~]$ sudo docker image rm -f hello-world:latest
[qiqi@node01 ~]$ sudo docker rmi -f hello-world:latest
```

## 根据`IMAGE ID`删除所有镜像

```shell
[qiqi@node01 ~]$ sudo docker image rm $(sudo docker images -a -q)
[qiqi@node01 ~]$ sudo docker rmi $(sudo docker images -a -q)
```

## 根据`IMAGE ID`强制删除所有镜像

```shell
[qiqi@node01 ~]$ sudo docker image rm -f $(sudo docker images -a -q)
[qiqi@node01 ~]$ sudo docker rmi -f $(sudo docker images -a -q)
```

## 保存镜像到本地

```shell
[qiqi@node01 ~]$ sudo docker save -o hello-world.tar hello-world:latest
```

## 从本地加载镜像到本地镜像仓库

```shell
[qiqi@node01 ~]$ sudo docker load -i hello-world.tar
```


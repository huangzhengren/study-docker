- [`docker`常用命令](#docker常用命令)
  - [查看`docker`版本](#查看docker版本)
  - [查看`docker`服务状态](#查看docker服务状态)
  - [启动`docker`服务](#启动docker服务)
  - [重启`docker`服务](#重启docker服务)
  - [停止`docker`服务](#停止docker服务)
  - [查看`docker`服务信息](#查看docker服务信息)
  - [拉取镜像](#拉取镜像)
  - [查看镜像列表](#查看镜像列表)
  - [运行镜像](#运行镜像)

# `docker`常用命令

## 查看`docker`版本

```shell
[qiqi@node01 ~]$ sudo docker version
[qiqi@node01 ~]$ sudo docker -v
[qiqi@node01 ~]$ sudo docker --version
```

## 查看`docker`服务状态

```shell
[qiqi@node01 ~]$ sudo systemctl status docker.service
```

## 启动`docker`服务

```shell
[qiqi@node01 ~]$ sudo systemctl start docker.service
```

## 重启`docker`服务

```shell
[qiqi@node01 ~]$ sudo systemctl restart docker.service
```

## 停止`docker`服务

```shell
[qiqi@node01 ~]$ sudo systemctl stop docker.service
```

## 查看`docker`服务信息

```shell
[qiqi@node01 ~]$ sudo docker info
```

## 拉取镜像

```shell
[qiqi@node01 ~]$ sudo docker pull hello-world
```

## 查看镜像列表

```shell
[qiqi@node01 ~]$ sudo docker images
```

## 运行镜像

```shell
[qiqi@node01 ~]$ sudo docker run hello-world
```
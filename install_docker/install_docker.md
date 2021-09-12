- [安装`docker`](#安装docker)
  - [卸载旧版本](#卸载旧版本)
  - [安装必要的一些系统工具](#安装必要的一些系统工具)
  - [添加软件源信息](#添加软件源信息)
  - [更新并安装`docker`](#更新并安装docker)
  - [查看`docker`版本](#查看docker版本)
  - [启动`docker`](#启动docker)
  - [验证`docker`是否正确安装](#验证docker是否正确安装)
  - [为`docker`设置开机自启动](#为docker设置开机自启动)

# 安装`docker`

## 卸载旧版本

```shell
[qiqi@node01 ~]$ sudo yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine podman runc
```

## 安装必要的一些系统工具

```shell
[qiqi@node01 ~]$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```

## 添加软件源信息

```shell
[qiqi@node01 ~]$ sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
[qiqi@node01 ~]$ sudo sed -i 's+download.docker.com+mirrors.aliyun.com/docker-ce+' /etc/yum.repos.d/docker-ce.repo
```

## 更新并安装`docker`

```shell
[qiqi@node01 ~]$ sudo yum makecache fast
[qiqi@node01 ~]$ sudo yum install docker-ce docker-ce-cli containerd.io
```

## 查看`docker`版本

```shell
[qiqi@node01 ~]$ sudo docker version
[qiqi@node01 ~]$ sudo docker -v
[qiqi@node01 ~]$ sudo docker --version
```

## 启动`docker`

```shell
[qiqi@node01 ~]$ sudo systemctl start docker
```

## 验证`docker`是否正确安装

```shell
[qiqi@node01 ~]$ sudo docker run hello-world
```

## 为`docker`设置开机自启动

```shell
[qiqi@node01 ~]$ sudo systemctl enable docker.service
[qiqi@node01 ~]$ sudo systemctl list-unit-files | grep docker.service
```


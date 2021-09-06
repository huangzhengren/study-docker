- [`docker`网络命令](#docker网络命令)
  - [查看`docker`网络命令帮助信息](#查看docker网络命令帮助信息)
  - [查看网络列表](#查看网络列表)
  - [创建桥接网络](#创建桥接网络)
  - [创建网络时指定管理网络的驱动程序为桥接网络](#创建网络时指定管理网络的驱动程序为桥接网络)
  - [根据`NETWORK ID`查看网络元数据信息](#根据network-id查看网络元数据信息)
  - [根据`NAME`查看网络元数据信息](#根据name查看网络元数据信息)
  - [创建容器时指定网络](#创建容器时指定网络)
  - [根据`NAME`删除一个网络](#根据name删除一个网络)
  - [根据`NETWORK ID`删除一个网络](#根据network-id删除一个网络)

# `docker`网络命令

## 查看`docker`网络命令帮助信息

```shell
[qiqi@node01 ~]$ sudo docker network --help
```

## 查看网络列表

```shell
[qiqi@node01 ~]$ sudo docker network ls
```

## 创建桥接网络

```shell
[qiqi@node01 ~]$ sudo docker network create qiqi
```

## 创建网络时指定管理网络的驱动程序为桥接网络

```shell
[qiqi@node01 ~]$ sudo docker network create -d bridge qiqi
```

## 根据`NETWORK ID`查看网络元数据信息

```shell
[qiqi@node01 ~]$ sudo docker network inspect 38c81cc22424
```

## 根据`NAME`查看网络元数据信息

```shell
[qiqi@node01 ~]$ sudo docker network inspect qiqi
```

## 创建容器时指定网络

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 8080:8080 --network qiqi --name tomcat_qiqi tomcat:latest
```

## 根据`NAME`删除一个网络

```shell
[qiqi@node01 ~]$ sudo docker network rm qiqi
```

## 根据`NETWORK ID`删除一个网络

```shell
[qiqi@node01 ~]$ sudo docker network rm 38c81cc22424
```


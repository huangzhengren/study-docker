- [`docker`数据卷命令](#docker数据卷命令)
  - [根据`TAG`获取镜像元数据](#根据tag获取镜像元数据)
  - [根据`IMAGE ID`获取镜像元数据](#根据image-id获取镜像元数据)
  - [根据容器名称获取容器元数据](#根据容器名称获取容器元数据)
  - [根据`CONTAINER ID`获取容器元数据](#根据container-id获取容器元数据)
  - [显示数据卷列表](#显示数据卷列表)
  - [获取数据卷元数据](#获取数据卷元数据)
  - [创建自动数据卷](#创建自动数据卷)
  - [删除数据卷](#删除数据卷)
  - [删除所有未使用的本地卷](#删除所有未使用的本地卷)
  - [自定义数据卷目录运行容器](#自定义数据卷目录运行容器)
  - [自动数据卷目录运行容器](#自动数据卷目录运行容器)
  - [自动数据卷目录运行容器，数据卷目录宿主机可读写，容器内只读](#自动数据卷目录运行容器数据卷目录宿主机可读写容器内只读)
  - [根据容器名称进入容器](#根据容器名称进入容器)
  - [根据`CONTAINER ID`进入容器](#根据container-id进入容器)
  - [将容器打包成镜像](#将容器打包成镜像)
  - [备份镜像](#备份镜像)
  - [加载本地镜像到本地镜像仓库](#加载本地镜像到本地镜像仓库)
  - [静默加载本地镜像到本地镜像仓库](#静默加载本地镜像到本地镜像仓库)

# `docker`数据卷命令

## 根据`TAG`获取镜像元数据

```shell
[qiqi@node01 ~]$ sudo docker inspect hello-world
```

## 根据`IMAGE ID`获取镜像元数据

```shell
[qiqi@node01 ~]$ sudo docker inspect d1165f221234
```

## 根据容器名称获取容器元数据

```shell
[qiqi@node01 ~]$ sudo docker inspect tomcat_qiqi
```

## 根据`CONTAINER ID`获取容器元数据

```shell
[qiqi@node01 ~]$ sudo docker inspect 38f2191812ab
```

## 显示数据卷列表

```shell
[qiqi@node01 ~]$ sudo docker volume ls
```

## 获取数据卷元数据

```shell
[qiqi@node01 ~]$ sudo docker volume inspect qiqi
```

## 创建自动数据卷

```shell
[qiqi@node01 ~]$ sudo docker volume create qiqi
```

## 删除数据卷

```shell
[qiqi@node01 ~]$ sudo docker volume rm qiqi
```

## 删除所有未使用的本地卷

```shell
[qiqi@node01 ~]$ sudo docker volume prune
```

## 自定义数据卷目录运行容器

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 8080:8080 --name tomcat_qiqi -v /home/qiqi/qiqi:/usr/local/tomcat/webapps tomcat:latest
```

## 自动数据卷目录运行容器

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 8080:8080 -v qiqi:/usr/local/tomcat/webapps --name tomcat_qiqi tomcat:latest
```

## 自动数据卷目录运行容器，数据卷目录宿主机可读写，容器内只读

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 8080:8080 -v qiqi:/usr/local/tomcat/webapps:ro --name tomcat_qiqi tomcat:latest
```

## 根据容器名称进入容器

 ```shell
[qiqi@node01 ~]$ sudo docker exec -it tomcat_qiqi /bin/bash
 ```

## 根据`CONTAINER ID`进入容器

```shell
[qiqi@node01 ~]$ sudo docker exec -it 38f2191812ab /bin/bash
```

## 将容器打包成镜像

```shell
[qiqi@node01 ~]$ sudo docker commit -m "This is tomcat_qiqi." -a "huangzhengren" tomcat_qiqi tomcat_qiqi:forever
```

## 备份镜像

```shell
[qiqi@node01 ~]$ sudo docker save -o tomcat_qiqi.tar tomcat_qiqi:forever
```

## 加载本地镜像到本地镜像仓库

```shell
[qiqi@node01 ~]$ sudo docker load -i tomcat_qiqi.tar
```

## 静默加载本地镜像到本地镜像仓库

```shell
[qiqi@node01 ~]$ sudo docker load -q -i tomcat_qiqi.tar
```


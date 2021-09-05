- [`docker`容器常用命令](#docker容器常用命令)
  - [查看正在运行的容器](#查看正在运行的容器)
  - [查看所有的容器](#查看所有的容器)
  - [查看正在运行容器的`CONTAINER ID`](#查看正在运行容器的container-id)
  - [查看所有容器的`CONTAINER ID`](#查看所有容器的container-id)
  - [根据`NAMES`启动容器](#根据names启动容器)
  - [根据`CONTAINER ID`启动容器](#根据container-id启动容器)
  - [根据`NAMES`启动多个容器](#根据names启动多个容器)
  - [根据`CONTAINER ID`启动多个容器](#根据container-id启动多个容器)
  - [根据`NAMES`停止容器](#根据names停止容器)
  - [根据`CONTAINER ID`停止容器](#根据container-id停止容器)
  - [根据`NAMES`停止多个容器](#根据names停止多个容器)
  - [根据`CONTAINER ID`停止多个容器](#根据container-id停止多个容器)
  - [根据`NAMES`重启容器](#根据names重启容器)
  - [根据`CONTAINER ID`重启容器](#根据container-id重启容器)
  - [根据`NAMES`重启多个容器](#根据names重启多个容器)
  - [根据`CONTAINER ID`重启多个容器](#根据container-id重启多个容器)
  - [根据`NAMES`删除容器](#根据names删除容器)
  - [根据`NAMES`强制删除容器](#根据names强制删除容器)
  - [根据`CONTAINER ID`删除容器](#根据container-id删除容器)
  - [根据`CONTAINER ID`强制删除容器](#根据container-id强制删除容器)
  - [根据`NAMES`删除多个容器](#根据names删除多个容器)
  - [根据`NAMES`强制删除多个容器](#根据names强制删除多个容器)
  - [根据`CONTAINER ID`删除多个容器](#根据container-id删除多个容器)
  - [根据`CONTAINER ID`强制删除多个容器](#根据container-id强制删除多个容器)
  - [根据`CONTAINER ID`强制删除正在运行的容器](#根据container-id强制删除正在运行的容器)
  - [根据`CONTAINER ID`强制删除所有容器](#根据container-id强制删除所有容器)
  - [运行一个容器](#运行一个容器)
  - [根据`CONTAINER ID`启动容器](#根据container-id启动容器-1)
  - [根据`CONTAINER ID`停止容器](#根据container-id停止容器-1)
  - [运行容器并配置宿主机到容器的端口映射](#运行容器并配置宿主机到容器的端口映射)
  - [指定容器名称运行容器并配置宿主机到容器的端口映射](#指定容器名称运行容器并配置宿主机到容器的端口映射)
  - [指定容器名称后台运行容器并配置宿主机到容器的端口映射](#指定容器名称后台运行容器并配置宿主机到容器的端口映射)
  - [根据容器名称实时跟踪`docker`容器日志](#根据容器名称实时跟踪docker容器日志)
  - [根据`CONTAINER ID`实时跟踪`docker`容器日志](#根据container-id实时跟踪docker容器日志)
  - [根据容器名称实时跟踪`docker`容器日志并显示时间戳](#根据容器名称实时跟踪docker容器日志并显示时间戳)
  - [根据`CONTAINER ID`实时跟踪`docker`容器日志并显示时间戳](#根据container-id实时跟踪docker容器日志并显示时间戳)
  - [根据容器名称查看最后5行`docker`容器日志](#根据容器名称查看最后5行docker容器日志)
  - [根据`CONTAINER ID`查看最后5行`docker`容器日志](#根据container-id查看最后5行docker容器日志)
  - [根据容器名称以交互模式进入容器](#根据容器名称以交互模式进入容器)
  - [根据`CONTAINER ID`以交互模式进入容器](#根据container-id以交互模式进入容器)
  - [退出容器](#退出容器)

# `docker`容器常用命令

## 查看正在运行的容器

```shell
[qiqi@node01 ~]$ sudo docker ps
```

## 查看所有的容器

```shell
[qiqi@node01 ~]$ sudo docker ps -a
```

## 查看正在运行容器的`CONTAINER ID`

```shell
[qiqi@node01 ~]$ sudo docker ps -q
```

## 查看所有容器的`CONTAINER ID`

```shell
[qiqi@node01 ~]$ sudo docker ps -a -q
```

## 根据`NAMES`启动容器

```shell
[qiqi@node01 ~]$ sudo docker start nginx_qiqi
```

## 根据`CONTAINER ID`启动容器

```shell
[qiqi@node01 ~]$ sudo docker start ccd9394bf985
```

## 根据`NAMES`启动多个容器

```shell
[qiqi@node01 ~]$ sudo docker start nginx_qiqi redis_qiqi
```

## 根据`CONTAINER ID`启动多个容器

```shell
[qiqi@node01 ~]$ sudo docker start ccd9394bf985 f6973a04937c
```

## 根据`NAMES`停止容器

```shell
[qiqi@node01 ~]$ sudo docker stop nginx_qiqi
```

## 根据`CONTAINER ID`停止容器

```shell
[qiqi@node01 ~]$ sudo docker stop nginx_qiqi
```

## 根据`NAMES`停止多个容器

```shell
[qiqi@node01 ~]$ sudo docker stop nginx_qiqi redis_qiqi
```

## 根据`CONTAINER ID`停止多个容器

```shell
[qiqi@node01 ~]$ sudo docker stop f6973a04937c ccd9394bf985
```

## 根据`NAMES`重启容器

```shell
[qiqi@node01 ~]$ sudo docker restart nginx_qiqi
```

## 根据`CONTAINER ID`重启容器

```shell
[qiqi@node01 ~]$ sudo docker restart d518cd14fc74
```

## 根据`NAMES`重启多个容器

```shell
[qiqi@node01 ~]$ sudo docker restart nginx_qiqi redis_qiqi
```

## 根据`CONTAINER ID`重启多个容器

```shell
[qiqi@node01 ~]$ sudo docker restart d518cd14fc74 f6973a04937c
```

## 根据`NAMES`删除容器

```shell
[qiqi@node01 ~]$ sudo docker rm nginx_qiqi
```

## 根据`NAMES`强制删除容器

```shell
[qiqi@node01 ~]$ sudo docker rm -f nginx_qiqi
```

## 根据`CONTAINER ID`删除容器

```shell
[qiqi@node01 ~]$ sudo docker rm ccd9394bf985
```

## 根据`CONTAINER ID`强制删除容器

```shell
[qiqi@node01 ~]$ sudo docker rm -f ccd9394bf985
```

## 根据`NAMES`删除多个容器

```shell
[qiqi@node01 ~]$ sudo docker rm nginx_qiqi redis_qiqi
```

## 根据`NAMES`强制删除多个容器

```shell
[qiqi@node01 ~]$ sudo docker rm -f nginx_qiqi redis_qiqi
```

## 根据`CONTAINER ID`删除多个容器

```shell
[qiqi@node01 ~]$ sudo docker rm ccd9394bf985 f6973a04937c
```

## 根据`CONTAINER ID`强制删除多个容器

```shell
[qiqi@node01 ~]$ sudo docker rm -f ccd9394bf985 f6973a04937c
```

## 根据`CONTAINER ID`强制删除正在运行的容器

```shell
[qiqi@node01 ~]$ sudo docker rm -f $(sudo docker ps -q)
```

## 根据`CONTAINER ID`强制删除所有容器

```shell
[qiqi@node01 ~]$ sudo docker rm -f $(sudo docker ps -a -q)
```

## 运行一个容器

```shell
[qiqi@node01 ~]$ sudo docker run hello-world
```

## 根据`CONTAINER ID`启动容器

```shell
[qiqi@node01 ~]$ sudo docker start 11978e8bb713
```

## 根据`CONTAINER ID`停止容器

```shell
[qiqi@node01 ~]$ sudo docker stop 11978e8bb713
```

## 运行容器并配置宿主机到容器的端口映射

```shell
[qiqi@node01 ~]$ sudo docker run -p 80:80 nginx:latest
```

## 指定容器名称运行容器并配置宿主机到容器的端口映射

```shell
[qiqi@node01 ~]$ sudo docker run -p 80:80 --name nginx_qiqi nginx:latest
```

## 指定容器名称后台运行容器并配置宿主机到容器的端口映射

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 80:80 --name nginx_qiqi nginx:latest
```

## 根据容器名称实时跟踪`docker`容器日志

```shell
[qiqi@node01 ~]$ sudo docker logs -f nginx_qiqi
```

## 根据`CONTAINER ID`实时跟踪`docker`容器日志

```shell
[qiqi@node01 ~]$ sudo docker logs -f d518cd14fc74
```

## 根据容器名称实时跟踪`docker`容器日志并显示时间戳

```shell
[qiqi@node01 ~]$ sudo docker logs -f -t nginx_qiqi
```

## 根据`CONTAINER ID`实时跟踪`docker`容器日志并显示时间戳

```shell
[qiqi@node01 ~]$ sudo docker logs -f -t d518cd14fc74
```

## 根据容器名称查看最后5行`docker`容器日志

```shell
[qiqi@node01 ~]$ sudo docker logs -n 5 nginx_qiqi
```

## 根据`CONTAINER ID`查看最后5行`docker`容器日志

```shell
[qiqi@node01 ~]$ sudo docker logs -n 5 d518cd14fc74
```

## 根据容器名称以交互模式进入容器

```shell
[qiqi@node01 ~]$ sudo docker exec -it nginx_qiqi /bin/bash
```

## 根据`CONTAINER ID`以交互模式进入容器

```shell
[qiqi@node01 ~]$ sudo docker exec -it d518cd14fc74 /bin/bash
```

## 退出容器

```shell
root@d518cd14fc74:/# exit
```


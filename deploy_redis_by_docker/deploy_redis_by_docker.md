- [通过`docker`部署`redis`](#通过docker部署redis)
  - [通过`docker`部署`redis`](#通过docker部署redis-1)
    - [拉取镜像](#拉取镜像)
    - [运行一个`redis`容器，指定用于存放数据的自动数据卷并开启`aof`持久化](#运行一个redis容器指定用于存放数据的自动数据卷并开启aof持久化)
  - [自定义配置文件启动`redis`](#自定义配置文件启动redis)
    - [创建用于存放`redis`数据的自动数据卷](#创建用于存放redis数据的自动数据卷)
    - [创建用于存放`redis`配置文件的自动数据卷](#创建用于存放redis配置文件的自动数据卷)
    - [去官网下载对应`redis`版本的配置文件，上传到`redis`配置文件的数据卷目录中](#去官网下载对应redis版本的配置文件上传到redis配置文件的数据卷目录中)
    - [运行一个`redis`容器,指定用于存放数据和配置文件的自动数据卷](#运行一个redis容器指定用于存放数据和配置文件的自动数据卷)

# 通过`docker`部署`redis`

## 通过`docker`部署`redis`

### 拉取镜像

```shell
[qiqi@node01 ~]$ sudo docker pull redis
```

### 运行一个`redis`容器，指定用于存放数据的自动数据卷并开启`aof`持久化

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 6379:6379 -v redis_data_qiqi:/data --name redis_qiqi redis redis-server --appendonly yes
```

## 自定义配置文件启动`redis`

### 创建用于存放`redis`数据的自动数据卷

```shell
[qiqi@node01 ~]$ sudo docker volume create redis_data_qiqi
```

### 创建用于存放`redis`配置文件的自动数据卷

```shell
[qiqi@node01 ~]$ sudo docker volume create redis_config_qiqi
```

### 去官网下载对应`redis`版本的配置文件，上传到`redis`配置文件的数据卷目录中

```shell
[qiqi@node01 ~]$ sudo cp redis.conf /var/lib/docker/volumes/redis_config_qiqi/_data
```

### 运行一个`redis`容器,指定用于存放数据和配置文件的自动数据卷

```shell
[qiqi@node01 _data]$ sudo docker run -dit -p 6379:6379 -v redis_data_qiqi:/data -v redis_config_qiqi:/usr/local/etc/redis --name redis_qiqi redis redis-server /usr/local/etc/redis/redis.conf
```




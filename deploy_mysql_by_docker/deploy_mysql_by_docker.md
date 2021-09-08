- [通过`docker`部署`mysql`](#通过docker部署mysql)
  - [通过`docker`部署`mysql`](#通过docker部署mysql-1)
    - [拉取镜像](#拉取镜像)
    - [创建一个`mysql`容器,指定存放`mysql`数据、配置文件的自动数据卷并指定密码](#创建一个mysql容器指定存放mysql数据配置文件的自动数据卷并指定密码)
  - [其他相关命令](#其他相关命令)
    - [创建一个允许空密码登录的`mysql`容器](#创建一个允许空密码登录的mysql容器)
    - [创建一个随机密码的`mysql`容器](#创建一个随机密码的mysql容器)
    - [创建一个带密码的`mysql`容器](#创建一个带密码的mysql容器)
    - [创建一个`mysql`容器,指定自定义数据卷和密码](#创建一个mysql容器指定自定义数据卷和密码)
    - [创建一个`mysql`容器,指定自动数据卷和密码](#创建一个mysql容器指定自动数据卷和密码)

# 通过`docker`部署`mysql`

## 通过`docker`部署`mysql`

### 拉取镜像

```shell
[qiqi@node01 ~]$ sudo docker pull mysql:5.7.35
```

### 创建一个`mysql`容器,指定存放`mysql`数据、配置文件的自动数据卷并指定密码

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 3306:3306 -e MYSQL_ROOT_PASSWORD=qiqi -v data_qiqi:/var/lib/mysql -v config_qiqi:/etc/mysql --name mysql_qiqi mysql:5.7.35
```

## 其他相关命令

### 创建一个允许空密码登录的`mysql`容器

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 3306:3306 -e MYSQL_ALLOW_EMPTY_PASSWORD=yes --name mysql_qiqi mysql:5.7.35
```

### 创建一个随机密码的`mysql`容器

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 3306:3306 -e MYSQL_RANDOM_ROOT_PASSWORD=yes --name mysql_qiqi mysql:5.7.35
```

### 创建一个带密码的`mysql`容器

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 3306:3306 -e MYSQL_ROOT_PASSWORD=qiqi --name mysql_qiqi mysql:5.7.35
```

### 创建一个`mysql`容器,指定自定义数据卷和密码

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 3306:3306 -e MYSQL_ROOT_PASSWORD=qiqi -v /home/qiqi/qiqi:/var/lib/mysql --name mysql_qiqi mysql:5.7.35
```

### 创建一个`mysql`容器,指定自动数据卷和密码

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 3306:3306 -e MYSQL_ROOT_PASSWORD=qiqi -v qiqi:/var/lib/mysql --name mysql_qiqi mysql:5.7.35
```


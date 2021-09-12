- [部署`portainer`](#部署portainer)
  - [通过`docker run`部署`portainer`](#通过docker-run部署portainer)
    - [拉取镜像](#拉取镜像)
    - [创建数据卷](#创建数据卷)
    - [通过镜像运行容器](#通过镜像运行容器)
    - [浏览器访问http://IP:9000](#浏览器访问httpip9000)
    - [输入`admin`用户的密码并确认密码，点击Create user创建`admin`用户](#输入admin用户的密码并确认密码点击create-user创建admin用户)
    - [将`Portainer`连接到要管理的`Docker`环境，选择`Local`，点击`Connect`连接](#将portainer连接到要管理的docker环境选择local点击connect连接)
  - [通过`docker-compose`部署`portainer`](#通过docker-compose部署portainer)
    - [`docker-compose.yml`配置](#docker-composeyml配置)
    - [使用`docker-compose`后台运行`portainer`容器](#使用docker-compose后台运行portainer容器)

# 部署`portainer`

## 通过`docker run`部署`portainer`

### 拉取镜像

```shell
[qiqi@node01 ~]$ sudo docker pull portainer/portainer
```

### 创建数据卷

```shell
[qiqi@node01 ~]$ sudo docker volume create portainer_data
```

### 通过镜像运行容器

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 8000:8000 -p 9000:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data_qiqi:/data --name portainer_qiqi portainer/portainer
```

### 浏览器访问http://IP:9000

### 输入`admin`用户的密码并确认密码，点击Create user创建`admin`用户

### 将`Portainer`连接到要管理的`Docker`环境，选择`Local`，点击`Connect`连接

## 通过`docker-compose`部署`portainer`

### `docker-compose.yml`配置

```shell
version: "3.8"

services:
  portainer01:
    image: portainer/portainer
    container_name: portainer_qiqi
    ports:
      - "8000:8000"
      - "9000:9000"
    networks:
      - network_qiqi
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data_qiqi:/data

volumes:
  portainer_data_qiqi:
    external: false
networks:
  network_qiqi:
    external: false
```

### 使用`docker-compose`后台运行`portainer`容器

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml up -d
```


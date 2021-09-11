- [Dockerfile命令](#dockerfile命令)
  - [Dockerfile命令解析](#dockerfile命令解析)
    - [FROM](#from)
    - [RUN](#run)
    - [EXPOSE](#expose)
    - [WORKDIR](#workdir)
    - [COPY](#copy)
    - [ADD](#add)
    - [VOLUME](#volume)
    - [ENTRYPOINT](#entrypoint)
    - [CMD](#cmd)
    - [ENV](#env)
  - [构建镜像命令](#构建镜像命令)
    - [在当前目录构建自定义镜像](#在当前目录构建自定义镜像)
    - [指定目录构建自定义镜像](#指定目录构建自定义镜像)

# Dockerfile命令

## Dockerfile命令解析

### FROM

```shell
# 指定基于什么镜像构建
FROM centos:7 # 基于centos7镜像构建
```

### RUN

```shell
# 指定构建自定义镜像时运行的命令
RUN yum -y install vim # 在构建自定义镜像时运行的命令
RUM ["yum", "-y", "install", "vim"] # 在构建自定义镜像时运行的命令
```

### EXPOSE

```shell
# 为基于构建的镜像运行的容器指定对外暴露的端口
EXPOSE 1314 # 为基于构建的镜像运行的容器指定对外暴露的端口，默认为tcp
EXPOSE 520/tcp # 为基于构建的镜像运行的容器指定对外暴露的tcp端口
EXPOSE 521/udp # 为基于构建的镜像运行的容器指定对外暴露的udp端口
```

### WORKDIR 

```shell
# 为Dockfile中的任何RUN、CMD、ENTRYPOINT、COPY、ADD指令设置工作目录，如果在Dockerfile不存在，也会自动创建
WORKDIR /data # 绝对路径
WORKDIR qiqi # 相对路径，基于上一个WORKDIR来确定
```

### COPY

```shell
# 构建镜像的时候拷贝宿主机的文件或目录到镜像内
COPY qiqi.txt qiqi # 基于WORKDIR拷贝qiqi.txt为qiqi
COPY qiqi.txt dir_qiqi/ # 基于WORKDIR拷贝qiqi.txt为dir_qiqi/qiqi.txt
COPY qiqi.txt /qiqi/ # 拷贝qiqi.txt为/qiqi/qiqi.txt
COPY qiqi qiqi # 基于WORKDIR拷贝qiqi目录为qiqi
COPY qiqi xiaobudianer # 基于WORKDIR拷贝qiqi目录为xiaobudianer
```

### ADD

```shell
# 构建镜像的时候将文件、目录或者通过URL下载的压缩包添加到镜像内，如果宿主机是一个压缩包，在运行容器的时候，会自动解压压缩包
ADD qiqi xiaobudianer # 基于WORKDIR拷贝qiqi目录为xiaobudianer
ADD https://downloads.apache.org/tomcat/tomcat-10/v10.0.10/src/apache-tomcat-10.0.10-src.tar.gz qiqi/ # 基于WORKDIR，通过URL下载压缩包到qiqi目录里
ADD *.tar.gz qiqi/ # 基于WORKDIR,添加.tar.gz结尾的压缩包到qiqi目录里
ADD qiqi?.txt qiqi/ # 基于WORKDIR，使用?通配单个字符，添加文件到qiqi目录里
```

```shell
ADD apache-tomcat-10.0.10-src.tar.gz qiqi/ ## 先下载apache-tomcat-10.0.10-src.tar.gz到宿主机，然后加进Dockerfile里，构建镜像后，在运行容器的时候，会自动解压压缩包
```

### VOLUME

```shell
# 定义允许作为数据卷挂载到宿主机的目录
VOLUME /data/qiqi
VOLUME ["/data/qiqi"]
```

### ENTRYPOINT

```shell
# 设定容器启动时第一个运行的命令及其参数
ENTRYPOINT ["ls", "-a"]
```

### CMD

```shell
# 设置容器的默认执行的命令
CMD ["ls", "-a"]
```

### ENV

```shell
# ENV指令将环境变量<key>设置为值<value>
ENV QIQI_DIR /data/qiqi
ENV QIQI_DIR=/data/qiqi
```

## 构建镜像命令

### 在当前目录构建自定义镜像

```shell
[qiqi@node01 ~]$ sudo docker build -f Dockerfile -t centos:qiqi .
```

### 指定目录构建自定义镜像

```shell
[qiqi@node01 ~]$ sudo docker build -f Dockerfile -t centos:qiqi /home/qiqi/qiqi
```


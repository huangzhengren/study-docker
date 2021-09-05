- [`docker` 拷贝命令](#docker-拷贝命令)
  - [将文件或目录从容器中拷贝到宿主机](#将文件或目录从容器中拷贝到宿主机)
    - [根据容器名称将文件从容器中拷贝到宿主机的当前目录下](#根据容器名称将文件从容器中拷贝到宿主机的当前目录下)
    - [根据容器名称将文件从容器中拷贝到宿主机的当前目录下并改名](#根据容器名称将文件从容器中拷贝到宿主机的当前目录下并改名)
    - [根据容器名称将目录从容器中拷贝到宿主机的当前目录下](#根据容器名称将目录从容器中拷贝到宿主机的当前目录下)
    - [根据容器名称将目录从容器中拷贝到宿主机的当前目录下并改名](#根据容器名称将目录从容器中拷贝到宿主机的当前目录下并改名)
    - [根据`CONTAINER ID`将文件从容器中拷贝到宿主机的当前目录下](#根据container-id将文件从容器中拷贝到宿主机的当前目录下)
    - [根据`CONTAINER ID`将文件从容器中拷贝到宿主机的当前目录下并改名](#根据container-id将文件从容器中拷贝到宿主机的当前目录下并改名)
    - [根据`CONTAINER ID`将目录从容器中拷贝到宿主机的当前目录下](#根据container-id将目录从容器中拷贝到宿主机的当前目录下)
    - [根据`CONTAINER ID`将目录从容器中拷贝到宿主机的当前目录下并改名](#根据container-id将目录从容器中拷贝到宿主机的当前目录下并改名)
  - [将文件或目录从宿主机拷贝到容器中](#将文件或目录从宿主机拷贝到容器中)
    - [根据容器名称将文件从宿主机拷贝到容器中](#根据容器名称将文件从宿主机拷贝到容器中)
    - [根据容器名称将文件从宿主机拷贝到容器中并改名](#根据容器名称将文件从宿主机拷贝到容器中并改名)
    - [根据容器名称将目录从宿主机拷贝到容器中](#根据容器名称将目录从宿主机拷贝到容器中)
    - [根据容器名称将目录从宿主机拷贝到容器中并改名](#根据容器名称将目录从宿主机拷贝到容器中并改名)
    - [根据`CONTAINER ID`将文件从宿主机拷贝到容器中](#根据container-id将文件从宿主机拷贝到容器中)
    - [根据`CONTAINER ID`将文件从宿主机拷贝到容器中并改名](#根据container-id将文件从宿主机拷贝到容器中并改名)
    - [根据`CONTAINER ID`将目录从宿主机拷贝到容器中](#根据container-id将目录从宿主机拷贝到容器中)
    - [根据`CONTAINER ID`将目录从宿主机拷贝到容器中并改名](#根据container-id将目录从宿主机拷贝到容器中并改名)

# `docker` 拷贝命令

## 将文件或目录从容器中拷贝到宿主机

### 根据容器名称将文件从容器中拷贝到宿主机的当前目录下

```shell
[qiqi@node01 ~]$ sudo docker cp tomcat_qiqi:/usr/local/tomcat/qiqi.txt ./
```

### 根据容器名称将文件从容器中拷贝到宿主机的当前目录下并改名

```shell
[qiqi@node01 ~]$ sudo docker cp tomcat_qiqi:/usr/local/tomcat/qiqi.txt ./xiaobudianer.txt
```

### 根据容器名称将目录从容器中拷贝到宿主机的当前目录下

```shell
[qiqi@node01 ~]$ sudo docker cp tomcat_qiqi:/usr/local/tomcat/qiqi ./
```

### 根据容器名称将目录从容器中拷贝到宿主机的当前目录下并改名

```shell
[qiqi@node01 ~]$ sudo docker cp tomcat_qiqi:/usr/local/tomcat/qiqi ./xiaobudianer
```

### 根据`CONTAINER ID`将文件从容器中拷贝到宿主机的当前目录下

```shell
[qiqi@node01 ~]$ sudo docker cp 38f2191812ab:/usr/local/tomcat/qiqi.txt ./
```

### 根据`CONTAINER ID`将文件从容器中拷贝到宿主机的当前目录下并改名

```shell
[qiqi@node01 ~]$ sudo docker cp 38f2191812ab:/usr/local/tomcat/qiqi.txt ./xiaobudianer.txt
```

### 根据`CONTAINER ID`将目录从容器中拷贝到宿主机的当前目录下

```shell
[qiqi@node01 ~]$ sudo docker cp 38f2191812ab:/usr/local/tomcat/qiqi ./
```

### 根据`CONTAINER ID`将目录从容器中拷贝到宿主机的当前目录下并改名

```shell
[qiqi@node01 ~]$ sudo docker cp 38f2191812ab:/usr/local/tomcat/qiqi ./xiaobudianer
```

## 将文件或目录从宿主机拷贝到容器中

### 根据容器名称将文件从宿主机拷贝到容器中

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi.txt tomcat_qiqi:/usr/local/tomcat
```

### 根据容器名称将文件从宿主机拷贝到容器中并改名

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi.txt tomcat_qiqi:/usr/local/tomcat/xiaobudianer.txt
```

### 根据容器名称将目录从宿主机拷贝到容器中

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi tomcat_qiqi:/usr/local/tomcat
```

### 根据容器名称将目录从宿主机拷贝到容器中并改名

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi tomcat_qiqi:/usr/local/tomcat/xiaobudianer
```

### 根据`CONTAINER ID`将文件从宿主机拷贝到容器中

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi.txt 38f2191812ab:/usr/local/tomcat
```

### 根据`CONTAINER ID`将文件从宿主机拷贝到容器中并改名

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi.txt 38f2191812ab:/usr/local/tomcat/xiaobudianer.txt
```

### 根据`CONTAINER ID`将目录从宿主机拷贝到容器中

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi 38f2191812ab:/usr/local/tomcat
```

### 根据`CONTAINER ID`将目录从宿主机拷贝到容器中并改名

```shell
[qiqi@node01 ~]$ sudo docker cp qiqi 38f2191812ab:/usr/local/tomcat/xiaobudianer
```
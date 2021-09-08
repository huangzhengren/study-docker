- [通过`docker`部署`tomcat`](#通过docker部署tomcat)
  - [拉取`tomcat`镜像](#拉取tomcat镜像)
  - [运行一个`tomcat`容器,指定存放`tomcat`应用、配置文件的自动数据卷](#运行一个tomcat容器指定存放tomcat应用配置文件的自动数据卷)

# 通过`docker`部署`tomcat`

## 拉取`tomcat`镜像

```shell
[qiqi@node01 _data]$ sudo docker pull tomcat
```

## 运行一个`tomcat`容器,指定存放`tomcat`应用、配置文件的自动数据卷

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 8080:8080 -v tomcat_data_qiqi:/usr/local/tomcat/webapps -v tomcat_config_qiqi:/usr/local/tomcat/conf --name tomcat_qiqi tomcat 
```


- [通过`docker`部署`elasticsearch`](#通过docker部署elasticsearch)
  - [拉取`elasticsearch`镜像](#拉取elasticsearch镜像)
  - [创建一个桥接网络](#创建一个桥接网络)
  - [使用新建的桥接网络，以单节点运行`elasticsearch`容器，指定存放数据、配置文件和插件的数据卷](#使用新建的桥接网络以单节点运行elasticsearch容器指定存放数据配置文件和插件的数据卷)
  - [安装`wget`和`unzip`](#安装wget和unzip)
  - [下载对应版本`ik`分词器](#下载对应版本ik分词器)
  - [在存放插件的数据卷建立`ik`目录](#在存放插件的数据卷建立ik目录)
  - [将`ik`分词器插件解压到`ik`目录中](#将ik分词器插件解压到ik目录中)
  - [设置`vm.max_map_count`的值](#设置vmmax_map_count的值)
  - [重新加载内核参数配置](#重新加载内核参数配置)
  - [重启`elasticsearch`容器](#重启elasticsearch容器)
  - [查看`elasticsearch`容器启动日志](#查看elasticsearch容器启动日志)
  - [拉取`kibana`镜像](#拉取kibana镜像)
  - [指定桥接网络运行`kibana`镜像，指定存放配置文件的数据卷](#指定桥接网络运行kibana镜像指定存放配置文件的数据卷)
  - [修改`kibana.yml`文件](#修改kibanayml文件)
  - [重启`kibana`容器](#重启kibana容器)
- [可能遇到的错误](#可能遇到的错误)

# 通过`docker`部署`elasticsearch`

## 拉取`elasticsearch`镜像

```shell
[qiqi@node01 ~]$ sudo docker pull elasticsearch:7.14.0
```

## 创建一个桥接网络

```shell
[qiqi@node01 ~]$ sudo docker network create -d bridge network_qiqi
```

## 使用新建的桥接网络，以单节点运行`elasticsearch`容器，指定存放数据、配置文件和插件的数据卷

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 9200:9200 -p 9300:9300 --network network_qiqi -e "discovery.type=single-node" -v es_data_qiqi:/usr/share/elasticsearch/data -v es_config_qiqi:/usr/share/elasticsearch/config -v es_plugins_qiqi:/usr/share/elasticsearch/plugins --name es_qiqi elasticsearch:7.14.0
```

## 安装`wget`和`unzip`

```shell
[qiqi@node01 ~]$ sudo yum -y install wget unzip
```

## 下载对应版本`ik`分词器

```shell
[qiqi@node01 ~]$ sudo wget https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.14.0/elasticsearch-analysis-ik-7.14.0.zip
```

## 在存放插件的数据卷建立`ik`目录

```shell
[qiqi@node01 ~]$ sudo mkdir -p /var/lib/docker/volumes/es_plugins_qiqi/_data/ik
```

## 将`ik`分词器插件解压到`ik`目录中

```shell
[qiqi@node01 ~]$ sudo unzip elasticsearch-analysis-ik-7.14.0.zip -d /var/lib/docker/volumes/es_plugins_qiqi/_data/ik
```

## 设置`vm.max_map_count`的值

```shell
[qiqi@node01 ~]$ echo "vm.max_map_count = 262144" | sudo tee -a /etc/sysctl.conf
```

## 重新加载内核参数配置

```shell
[qiqi@node01 ~]$ sudo sysctl -p
```

## 重启`elasticsearch`容器

```shell
[qiqi@node01 ~]$ sudo docker restart es_qiqi
```

## 查看`elasticsearch`容器启动日志

```shell
[qiqi@node01 ~]$ sudo docker logs -f es_qiqi
```

## 拉取`kibana`镜像

```shell
[qiqi@node01 ~]$ sudo docker pull kibana:7.14.0
```

## 指定桥接网络运行`kibana`镜像，指定存放配置文件的数据卷

```shell
[qiqi@node01 ~]$ sudo docker run -dit -p 5601:5601 --network network_qiqi -v kibana_config_qiqi:/usr/share/kibana/config --name kibana_qiqi kibana:7.14.0
```

## 修改`kibana.yml`文件

```shell
[qiqi@node01 ~]$ sudo sed -i "s/http:\/\/elasticsearch:9200/http:\/\/172.18.0.2:9200/" /var/lib/docker/volumes/kibana_config_qiqi/_data/kibana.yml
```

## 重启`kibana`容器

```shell
[qiqi@node01 ~]$ sudo docker restart kibana_qiqi
```

# 可能遇到的错误

```
ERROR: [2] bootstrap checks failed. You must address the points described in the following [2] lines before starting Elasticsearch.
bootstrap check failure [1] of [2]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
bootstrap check failure [2] of [2]: the default discovery settings are unsuitable for production use; at least one of [discovery.seed_hosts, discovery.seed_providers, cluster.initial_master_nodes] must be configured
ERROR: Elasticsearch did not exit normally - check the logs at /usr/share/elasticsearch/logs/docker-cluster.log
```


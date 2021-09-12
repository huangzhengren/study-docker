# docker-compose命令

## docker-compose.yml配置文件解析

```shell
version: "3.8" # 声明版本号


services: # 定义服务集
  tomcat01: # 定义单个服务实例
    image: tomcat_qiqi:forever # 基于tomcat_qiqi:forever镜像
    container_name: tomcat_qiqi01 # 指定容器名称
    ports: # 指定端口映射
      - "8080:8080"
    networks: # 指定网络
      - network_qiqi
    volumes: # 指定数据卷
      - tomcat01:/usr/local/tomcat/webapps
    depends_on: # 指定服务之间的依赖关系
      - mysql01
      - redis01
      - tomcat02
    healthcheck: # 心跳检测
      test: ["CMD", "curl", "-f", "http://localhost:8080"]
      interval: 1m30s # 间隔多久进行一次心跳检测
      timeout: 10s # 执行命令超时时间
      retries: 3 # 连续检查次数，超过retries次数则认为该容器unhealthy
      start_period: 40s # 为需要启动的容器提供了初始化的时间段， 在这个时间段内如果检查失败， 则不会记录失败次数。 如果在启动时间内成功执行了健康检查， 则容器将被视为已经启动， 如果在启动时间内再次出现检查失败， 则会记录失败次数。

  tomcat02:
    image: tomcat_qiqi:forever
    container_name: tomcat_qiqi02
    ports:
      - "8081:8080"
    networks:
      - network_qiqi
    volumes:
      - tomcat02:/usr/local/tomcat/webapps

  mysql01:
    image: mysql:5.7.35
    container_name: mysql_qiqi01
    ports:
      - "3306:3306"
    networks:
      - network_qiqi
    volumes:
      - mysql_data01:/var/lib/mysql
      - mysql_config01:/etc/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=qiqi # 定义环境变量 
    # env_file: # 环境变量文件，使用这个选项可将环境变量和docker-compose.yml文件分离，必须以.env结尾
    #  - ./mysql_config_qiqi.env
  redis01:
    image: redis:latest
    container_name: redis_qiqi01
    ports:
      - 6379:6379
    networks:
      - network_qiqi
    volumes:
      - redis_data01:/data
    command: redis-server --appendonly yes # 覆盖默认命令
    ulimits: # 覆盖容器的默认ulimits
      nproc: 65535
      nofile:
        soft: 20000
        hard: 40000
  app01:
    build: # 先根据Dockerfile构建镜像再运行镜像
      context: ./ # 指定上下文目录
      dockerfile: ./Dockerfile # Dockerfile文件名称
    container_name: app_qiqi01
    ports:
      - "8082:8080"
    networks:
      - network_qiqi
     
     
volumes: # 定义数据卷
  tomcat01:
    external: false
  tomcat02:
    external: false
  mysql_data01:
    external: false
  mysql_config01:
    external: false
  redis_data01:
    external: false


networks: # 定义网络
  network_qiqi:
    external: true
```

### `docker-compose`运行所有容器

```shell
[qiqi@node01 ~]$ sudo docker-compose up
```

## `docker-compose`指定`docker-compose.yml`文件运行所有容器

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml up
```

## `docker-compose`指定`docker-compose.yml`文件后台运行所有容器

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml up -d
```

## 根据服务实例名称，使用`docker-compose`后台运行单个容器

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml up -d redis01
```

## 根据服务实例名称，使用`docker-compose`后台运行多个容器

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml up -d tomcat01 mysql01
```

## 根据服务实例名称，使用`docker-compose`登录到容器终端

```shell
[qiqi@node01 ~]$ sudo docker-compose exec mysql01 /bin/bash
```

## 列出通过`docker-compose`命令启动的容器

```
[qiqi@node01 ~]$ sudo docker-compose ps
```

## 停止通过up命令启动的所有容器，并移除容器和网络

```shell
[qiqi@node01 ~]$ sudo docker-compose docker-compose.yml down
```

## 重启所有服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml restart
```

## 根据服务实例名称重启单个服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml restart tomcat01
```

## 根据服务实例名称重启多个服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml restart tomcat01
```

## 根据服务实例名称删除服务

```shell
[qiqi@node01 ~]$ sudo docker-compose rm app01
```

## 根据服务实例名称停止单个服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml stop tomcat01 tomcat02
```

## 根据服务实例名称停止多个服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml stop tomcat01 tomcat02
```

## 根据服务实例名称停止所有服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml stop
```

## 根据服务实例名称启用单个服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml start redis01
```

## 根据服务实例名称启用多个服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml start mysql01 tomcat01
```

## 根据服务实例名称启用所有服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml start
```

## 根据服务实例名称删除服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml rm redis01
```

## 根据服务实例名称查看某个容器资源使用情况

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml top tomcat01
```

## 根据服务实例名称查看多个容器资源使用情况

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml top tomcat01 tomcat02
```

## 根据服务实例名称查看所有容器资源使用情况

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml top
```

## 根据服务实例名称暂停某个容器服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml pause tomcat01
```

## 根据服务实例名称暂停多个容器服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml pause tomcat02 redis01
```

## 根据服务实例名称暂停所有容器服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml pause
```

## 根据服务实例名称恢复某个容器服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml unpause tomcat01
```

## 根据服务实例名称恢复多个容器服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml unpause tomcat02 redis01
```

## 根据服务实例名称恢复所有容器服务

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml unpause
```

## 根据服务实例名称查看某个容器日志

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml logs -f mysql01
```

## 根据服务实例名称查看多个容器日志

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml logs -f mysql01 redis01
```

## 根据服务实例名称查看所有容器日志

```shell
[qiqi@node01 ~]$ sudo docker-compose -f docker-compose.yml logs -f
```


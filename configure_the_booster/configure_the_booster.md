- [配置镜像加速器](#配置镜像加速器)
  - [配置阿里云镜像加速器](#配置阿里云镜像加速器)
  - [守护进程重新加载](#守护进程重新加载)
  - [重启`docker`](#重启docker)
  - [查看`docker`服务信息](#查看docker服务信息)

# 配置镜像加速器

## 配置阿里云镜像加速器

```shell
[qiqi@node01 ~]$ sudo mkdir -p /etc/docker
[qiqi@node01 ~]$ sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://2r3tctoz.mirror.aliyuncs.com"]
}
EOF
```

## 守护进程重新加载

```shell
[qiqi@node01 ~]$ sudo systemctl daemon-reload
```

## 重启`docker`

```shell
[qiqi@node01 ~]$ sudo systemctl restart docker
```

## 查看`docker`服务信息

```shell
[qiqi@node01 ~]$ sudo docker info
```


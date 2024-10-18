# docker 常用镜像、启动命令

## Redis

[镜像配置](https://github.com/redis/docker-library-redis/blob/e5650da99bb377b2ed4f9f1ef993ff24729b1c16/7.2/debian/Dockerfile)

```sh
docker run -d --name redis726 \
-v /Users/admin/docker_container/data/redis:/data \
-p 6379:6379 \
redis:7.2.6 redis-server --appendonly yes --requirepass "123456"
```

## MySQL

```sh
docker run -d --name mysql57 \
-e MYSQL_ROOT_PASSWORD=123456 \
-p 3306:3306 \
-v /my/own/datadir:/var/lib/mysql \
mysql:5.7
```

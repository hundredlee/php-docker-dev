FROM alpine:latest
MAINTAINER hundredlee hundred9411@gmail.com

# 软件包安装
RUN apk add redis

ADD redis.conf /etc/redis.conf

# 端口号配置
EXPOSE 6379

# 容器命令执行
ENTRYPOINT ["redis-server","/etc/redis.conf"]
FROM alpine:latest
MAINTAINER hundredlee hundred9411@gmail.com

RUN echo -e "http://mirrors.ustc.edu.cn/alpine/latest-stable/main\n\
http://mirrors.ustc.edu.cn/alpine/latest-stable/community" > /etc/apk/repositories

# 软件包安装
RUN apk update && apk add redis

ADD redis.conf /etc/redis.conf

# 端口号配置
EXPOSE 6379

# 容器命令执行
ENTRYPOINT ["redis-server","/etc/redis.conf"]
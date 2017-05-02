[TOC]
## 开发环境Docker化 之 世界上最好的语言
>* 本文针对Mac用户，windows用户请绕行。
>
>* https://github.com/hundredlee/docker-compose github地址
>
>* 欢迎贡献代码


## 安装Docker环境
> http://docker.io/ 下载Mac桌面版
> 
> 怎么下载大家都知道的，不解释

## 获取docker开发环境脚本
>* ``` git clone git@github.com:hundredlee/docker-compose.git ```
>
>* 目录结构如下

```
├── app
│   └── demo
│       └── public
│           └── index.php
├── docker-compose.yml
└── services
    ├── console
    │   ├── Dockerfile
    │   └── composer.phar
    ├── php
    │   ├── Dockerfile
    │   └── config
    │       ├── opcache.ini
    │       ├── php.ini
    │       └── redis.conf
    └── web
        └── config
            └── demo.conf
```
## 运行demo项目
> 打开iTerms 进入根目录，并顺序运行以下两条命令
> 
> ``` docker-compose build ```
> 
> ``` docker-compose up -d ```
> 
> 打开浏览器访问 http://demo.dev
> 如果你看到了```phpinfo();```的界面，那么你已经成功了。

## 添加本地开发项目
- 1.打开docker-compose.yml
- 2.找到services -> php -> volumes
- 3.添加映射本地开发项目的绝对路径至容器的目录（目前我是直接映射到容器的/mnt目录，没毛病）
- 4.例如 ```- /Users/hundredlee/PHPStorm/project:/mnt/project```

## 新建并添加nginx配置文件
> 配置文件模板

```
server {
  listen       80;
  server_name  demo.dev;
  root          /mnt/demo/public;
  index         index.php;

  location / {
     try_files $uri $uri/ /index.php?$query_string;
   }

  location ~ \.php$ {
     fastcgi_pass   php:9000;
     fastcgi_index  index.php;
     fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
     include        fastcgi_params;
  }
}

```
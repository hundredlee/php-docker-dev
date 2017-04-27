FROM geshan/php7-alpine
MAINTAINER hundredlee <hundred9411@gmail.com>

WORKDIR /mnt/groups

RUN apk --update add wget \ 
	curl \
	git \
	grep \
	gmp-dev \
	libmcrypt-dev \
	freetype-dev \
	libxpm-dev \
	libwebp-dev \
	libjpeg-turbo-dev \
	libjpeg \
	bzip2-dev \
	openssl-dev \
	krb5-dev \
	libxml2-dev \
	build-base \
	tar \
	make \
	autoconf 

RUN apk --update add re2c bison curl-dev

# 把语言设置成简体中文
# RUN dpkg-reconfigure locales && \
#   locale-gen C.UTF-8 && \
#   /usr/sbin/update-locale LANG=C.UTF-8
# RUN echo 'zh_CN.UTF-8 UTF-8' >> /etc/locale.gen && \
#   locale-gen
# ENV LC_ALL C.UTF-8
# ENV LAN G zh_CN.UTF-8
# ENV LANGUAGE zh_CN.UTF-8

# 配置 git
RUN git config --global user.name "hundredlee" \
  && git config --global user.email "hundred9411@gmail.com"

#安装composer
COPY ./composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer
RUN echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
  && . ~/.bashrc \
  && composer config -g repo.packagist composer https://packagist.phpcomposer.com

CMD ["bash"]

ENTRYPOINT ["/bin/sh", "-c"]
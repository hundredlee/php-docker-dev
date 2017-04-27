FROM php:7.1
MAINTAINER hundredlee <hundred9411@gmail.com>


RUN apt-get update && apt-get install git

# 配置 git
RUN git config --global user.name "hundredlee" \
  && git config --global user.email "hundred9411@gmail.com"

#安装composer
COPY ./composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer
RUN echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
  && . ~/.bashrc \
  && composer config -g repo.packagist composer https://packagist.phpcomposer.com
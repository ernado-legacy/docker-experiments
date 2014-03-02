# http://nginx.org/download/nginx-1.5.10.tar.gz
FROM 	ubuntu:raring
MAINTAINER 	Alexandr Razumov ernado@ya.ru
# base for nginx spdy
RUN	sed -i 's/archive.ubuntu.com/mirror.yandex.ru/g' /etc/apt/sources.list
RUN	apt-get update
RUN	apt-get install wget make build-essential zlib1g-dev libpcre3 libpcre3-dev libbz2-dev libssl-dev -y
ENV NGINX_VER 1.5.10
RUN wget http://nginx.org/download/nginx-$NGINX_VER.tar.gz -nv
RUN tar -xf  nginx-$NGINX_VER.tar.gz 

# installing and building
RUN	cd nginx-$NGINX_VER && ./configure --with-http_spdy_module --with-http_ssl_module && make -j8 -s && make install

# creating dirs for configs and application static files
RUN	mkdir /etc/sites-enabled
RUN	mkdir /var/log/nginx
RUN mkdir /static

VOLUME /etc/sites-enabled
VOLUME /var/log/nginx
VOLUME /static

ADD nginx.conf /usr/local/nginx/conf/nginx.conf

EXPOSE 80 443
ENTRYPOINT 	["/usr/local/nginx/sbin/nginx"]

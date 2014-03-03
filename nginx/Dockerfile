# http://nginx.org/download/nginx-1.5.10.tar.gz
FROM 	cydev/cybuntu
MAINTAINER 	Alexandr Razumov ernado@ya.ru
# base for nginx spdy
# installing build dependencies
RUN	apt-get install zlib1g-dev libpcre3 libpcre3-dev libbz2-dev libssl-dev -y

# downloading and extracting nginx
ENV NGINX_VER 1.5.10
RUN wget http://nginx.org/download/nginx-$NGINX_VER.tar.gz -qO- | tar -zxf -

# installing and building
RUN	cd nginx-$NGINX_VER && ./configure --with-http_spdy_module --with-http_ssl_module && make -j8 -s && make install

# creating dirs for configs, logs, static
RUN	mkdir /etc/sites-enabled /var/log/nginx /static

# creating volumes for configs, logs, static
VOLUME ["/etc/sites-enabled", "/var/log/nginx", "/static"]

# replacing nginx configuration file (enabled gzip and matched roots to correct volumes)
ADD nginx.conf /usr/local/nginx/conf/nginx.conf

EXPOSE 80 443
ENTRYPOINT 	["/usr/local/nginx/sbin/nginx"]

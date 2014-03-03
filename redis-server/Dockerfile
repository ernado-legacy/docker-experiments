FROM 		ubuntu:raring
RUN	sed -i 's/archive.ubuntu.com/mirror.yandex.ru/g' /etc/apt/sources.list
RUN	apt-get update
RUN         apt-get -y install redis-server
EXPOSE      6379
ENTRYPOINT  ["/usr/bin/redis-server"]

FROM centos:6
RUN yum -y update && yum clean all
RUN yum -y install php-fpm php-mbstring php-mysql php-gd && yum clean all
RUN sed -e 's/127.0.0.1:9000/9000/' -e '/allowed_clients/d' -e '/catch_workers_output/s/^;//' -e '/error_log/d' -i /etc/php-fpm.d/www.conf

LABEL author="Wilie wahyu hidayat"

RUN mkdir -p /Users
RUN mkdir -p /Users/wiliewahyuhidayat
RUN mkdir -p /Users/wiliewahyuhidayat/Documents
RUN mkdir -p /Users/wiliewahyuhidayat/Documents/PHP
RUN mkdir -p /Users/wiliewahyuhidayat/Documents/PHP/docker-php-test

EXPOSE 9000
ENTRYPOINT /usr/sbin/php-fpm --nodaemonize
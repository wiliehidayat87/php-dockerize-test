FROM 8.3.8-fpm-alpine as php
RUN apk --no-cache add tzdata
RUN apk --update add ca-certificates
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN docker-php-ext-enable mysqli

LABEL author="Wilie wahyu hidayat"

RUN mkdir -p /Users
RUN mkdir -p /Users/wiliewahyuhidayat
RUN mkdir -p /Users/wiliewahyuhidayat/Documents
RUN mkdir -p /Users/wiliewahyuhidayat/Documents/PHP
RUN mkdir -p /Users/wiliewahyuhidayat/Documents/PHP/docker-php-test

WORKDIR /Users/wiliewahyuhidayat/Documents/PHP/docker-php-test
COPY . .

FROM scratch

COPY --from=php /usr/share/zoneinfo /usr/share/zoneinfo
COPY --from=php /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --from=php /etc/passwd /etc/passwd
COPY --from=php /etc/group /etc/group
COPY --from=php /bin/sh /bin/sh

CMD ["php-fpm"]
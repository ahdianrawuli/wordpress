FROM alpine:latest

MAINTAINER "Ahdian Rawuli"

### START NGINX ###

ARG nginxversion
RUN apk add gcc g++ make libffi-dev openssl-dev pcre-dev zlib-dev libxml2-dev libzip-dev autoconf curl-dev libpng-dev wget tzdata openntpd netcat-openbsd bc curl git bash libressl
RUN cp /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
WORKDIR /root/
RUN wget "http://nginx.org/download/nginx-$nginxversion.tar.gz"
RUN tar xfvz nginx-$nginxversion.tar.gz
WORKDIR /root/nginx-$nginxversion
RUN ./configure --prefix=/opt/nginx --with-stream --with-threads --with-http_dav_module --with-ipv6 --with-file-aio --with-http_ssl_module --with-http_v2_module
RUN make -j $(nproc) && make install
RUN adduser -u 500 -HD nginx
RUN rm -rf /root/nginx*

### END NGINX ###

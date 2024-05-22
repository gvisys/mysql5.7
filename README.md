# MYSQL5.7 Dockerfile

• Baixe o mysql 5.7 \
```
FROM ubuntu:24.04
RUN apt -y update
RUN apt -y install wget net-tools iputils-ping nano unzip libtinfo5 libmecab2
WORKDIR /tmp
RUN wget http://dev.mysql.com/get/Downloads/MySql-5.7/mysql-server_5.7.28-1ubuntu19.04_amd64.deb-bundle.tar
RUN tar -xvf mysql-server_5.7.28-1ubuntu19.04_amd64.deb-bundle.tar
```

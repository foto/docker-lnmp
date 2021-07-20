# FROM daocloud.io/library/mysql:latest
FROM mysql:5.7.32

ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 3306
CMD ["mysqld"]
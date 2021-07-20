FROM redis:latest

ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    && echo "net.core.somaxconn=20480" >> /etc/sysctl.conf \

COPY redis.conf /usr/local/etc/redis/redis.conf
COPY redis.conf /usr/local/etc/redis.conf
CMD [ "redis-server", "/usr/local/etc/redis.conf" ]

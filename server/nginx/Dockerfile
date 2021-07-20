FROM nginx:stable

### set timezoßme
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 80
EXPOSE 81
EXPOSE 82
EXPOSE 83
EXPOSE 84
EXPOSE 85
EXPOSE 86
EXPOSE 90
EXPOSE 91
EXPOSE 92
EXPOSE 93
EXPOSE 443

ENTRYPOINT ["/docker-entrypoint.sh"]

STOPSIGNAL SIGQUIT

CMD ["nginx", "-g", "daemon off;"]
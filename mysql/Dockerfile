FROM mysql:5.7.16

# timezone
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY mysql.cnf /etc/mysql/conf.d/

CMD ["mysqld"]

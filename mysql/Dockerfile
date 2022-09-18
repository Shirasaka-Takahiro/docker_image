FROM mysql:8.0
ENV MYSQL_ROOT_PASSWORD="root"
RUN touch /var/run/mysqld/mysqld.sock
COPY db_setup.sql /docker-entrypoint-initdb.d/
COPY my.cnf /etc/mysql/conf.d/
EXPOSE 3306

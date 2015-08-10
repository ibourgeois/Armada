FROM armada/ubuntu
MAINTAINER Derek Bourgeois <derek@ibourgeois.com>

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y mysql-server
RUN rm -rf /var/lib/apt/lists/*

RUN sed -i 's/^\(bind-address\s.*\)/# \1/' /etc/mysql/my.cnf
RUN sed -i 's/^\(log_error\s.*\)/# \1/' /etc/mysql/my.cnf
RUN echo "mysqld_safe &" > /tmp/config
RUN echo "mysqladmin --silent --wait=30 ping || exit 1" >> /tmp/config
RUN echo "mysql -e 'GRANT ALL PRIVILEGES ON *.* TO \"root\"@\"%\" WITH GRANT OPTION;'" >> /tmp/config
RUN bash /tmp/config
RUN rm -f /tmp/config

VOLUME ["/etc/mysql", "/var/lib/mysql"]

WORKDIR /data

CMD ["mysqld_safe"]

EXPOSE 3306

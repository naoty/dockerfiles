FROM naoty/base
MAINTAINER Naoto Kaneko <naoty.k@gmail.com>

RUN apt-get install -y \
        mysql-server && \
    apt-get clean
ADD ./my.cnf /root/my.cnf
EXPOSE 3306
CMD ["service", "mysql", "start"]

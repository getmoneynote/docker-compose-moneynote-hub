FROM mysql:5.7

#ARG TZ=UTC
#ENV TZ ${TIMEZONE}
#RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ >/etc/timezone && chown -R mysql:root /var/lib/mysql/

COPY my.cnf /etc/mysql/conf.d/my.cnf
COPY init.sql /data/1.sql

RUN chmod 0444 /etc/mysql/conf.d/my.cnf
RUN chmod 0444 /data/1.sql
RUN chown $(whoami) /data/1.sql
RUN chgrp $(whoami) /data/1.sql

CMD ["mysqld"]

EXPOSE 3306

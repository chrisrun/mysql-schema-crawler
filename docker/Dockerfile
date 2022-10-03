FROM schemacrawler/schemacrawler:v16.18.2
 
USER root

RUN \
  apk add --update --no-cache \
  mariadb \
  mariadb-client \ 
  mariadb-server-utils pwgen && \
  rm -f /var/cache/apk/*

ADD my.cnf /etc/mysql/my.cnf


WORKDIR /home/schcrwlr 


COPY run.sh /scripts/run.sh
RUN mkdir /docker-entrypoint-initdb.d && \
    mkdir /scripts/pre-exec.d && \
    mkdir /scripts/pre-init.d && \
    chmod -R 755 /scripts

EXPOSE 3306


ENTRYPOINT ["/scripts/run.sh"]
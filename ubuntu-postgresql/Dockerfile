# PostgreSQL 9.3
# 
# 

FROM ubuntu:14.04

MAINTAINER Fernando Ike de Oliveira <fike@midstorm.org>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -qq

RUN apt-get update 

# If you use another language, change the package. e.g. language-pack-es
# and run update-locale with language variable.
#RUN apt-get install language-pack-en -y

#RUN update-locale LANG=en_US.UTF-8 LC_MESSAGES=POSIX

RUN apt-get install postgresql-9.3 postgresql-client-9.3 postgresql-contrib-9.3 -y

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/

USER postgres

RUN  /etc/init.d/postgresql start &&\
    psql --command "ALTER USER postgres with password 'foobar';"

RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.3/main/pg_hba.conf

RUN echo "listen_addresses='*'" >> /etc/postgresql/9.3/main/postgresql.conf

EXPOSE 5432

VOLUME  ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]

CMD ["/usr/lib/postgresql/9.3/bin/postgres", "-D", "/var/lib/postgresql/9.3/main", "-c", "config_file=/etc/postgresql/9.3/main/postgresql.conf"]


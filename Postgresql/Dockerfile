FROM postgres:11
LABEL maintainer="ovidio.zea@gmail.com"

ENV POSTGRES_PASSWORD=postgres123
ENV POSTGRES_DB=tienda

COPY ./scripts/ /docker-entrypoint-initdb.d/
#RUN psql -h localhost -U postgres -a -f /docker-entrypoint-initdb.d/scripts/DDL1.sql
CMD ["psql -h localhost -U postgres -a -f /docker-entrypoint-initdb.d/scripts/DDL1.sql"]
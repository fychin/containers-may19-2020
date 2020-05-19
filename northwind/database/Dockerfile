FROM mysql:5.7

# Set mysql root password
ENV MYSQL_ROOT_PASSWORD=checkit MYSQL_DATABASE=northwind

# Write one or more Docker commands to copy the sql files into /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

HEALTHCHECK --interval=30s --timeout=60s --start-period=40s --retries=3 \
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

# where MySQL stores the database
VOLUME /var/lib/mysql

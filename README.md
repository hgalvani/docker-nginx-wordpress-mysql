# docker-nginx-wordpress-mysql

## Generic stack for running wordpress cms with mysql and nginx.

After clonning, create an .env file. Fill empty variables

``PROJECT_NAME=
MYSQL_DBNAME=$PROJECT_NAME
MYSQL_USER=$PROJECT_NAME
MYSQL_PASSWORD=
MYSQL_ROOT_PASSWORD=
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=``


### Backup DB
``source .env
docker exec $(docker ps | grep mysql | awk '{print $1}') /usr/bin/mysqldump -u root --password=$MYSQL_ROOT_PASSWORD $MYSQL_DBNAME > ./backup/$MYSQL_DBNAME.sql``
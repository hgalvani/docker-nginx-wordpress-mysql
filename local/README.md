# docker-nginx-wordpress-mysql

Generic stack for running wordpress cms with mysql and nginx.

After clonning, create an .env file. Fill empty variables

```bash
PROJECT_NAME=
MYSQL_HOST=db
MYSQL_PORT=3306
MYSQL_DBNAME=
MYSQL_USER=
MYSQL_PASSWORD=
NGINX_PORT=
NGINX_ALLOWED_IP_FOR_ADMIN=
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
```

Check config with
`docker-compose config`

Build stack
`docker-compose up -d`

Show stack
`docker-compose ps`

```bash
               Name                             Command               State                 Ports
---------------------------------------------------------------------------------------------------------------
local_app_1   docker-entrypoint.sh php-fpm     Up      0.0.0.0:9000->9000/tcp
local_db_1    docker-entrypoint.sh mysqld      Up      0.0.0.0:3306->3306/tcp, 33060/tcp
local_web_1   /docker-entrypoint.sh ngin ...   Up      0.0.0.0:80->80/tcp
```

Enter into a container
`docker-compose exec db bash`

## Backup DB

```bash
mkdir ./backup
source .env
docker-compose exec mysql mysqldump -uroot ---password=${MYSQL_ROOT_PASSWORD}  ${MYSQL_DBNAME} > ./backup/${MYSQL_DBNAME}.sql
```

## Clean stack

```bash
docker-compose down -v  
sudo rm -rf ./data/* ./logs/*
```

## Restore db

Add this line at then end of volumes declaration for db containers

```yaml
db:
        image: mysql:5.7
        ...
        volumes:
          ...
          - ./backup/<MYSQL_DBNAME>.sql:/docker-entrypoint-initdb.d/<MYSQL_DBNAME>sql
```

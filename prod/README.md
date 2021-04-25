# docker-nginx-wordpress-mysql

Generic stack for running wordpress cms with mysql and nginx.

After clonning, create an .env file. Fill empty variables

```bash
PROJECT_NAME=
MYSQL_HOST=
MYSQL_PORT=3306
MYSQL_DBNAME=
MYSQL_USER=
MYSQL_PASSWORD=
NGINX_PORT=
NGINX_ALLOWED_IP_FOR_ADMIN=
```

Check config with
`docker-compose config`

Build stack
`docker-compose up -d`

Display contenairs
`docker-compose ps`

```bash
              Name                             Command               State                 Ports
---------------------------------------------------------------------------------------------------------------
prod_app_1   docker-entrypoint.sh php-fpm     Up      0.0.0.0:9000->9000/tcp
prod_web_1   /docker-entrypoint.sh ngin ...   Up      0.0.0.0:80->80/tcp
```

## Clean stack

```bash
docker-compose down -v  
sudo rm -rf ./data/* ./logs/*
```

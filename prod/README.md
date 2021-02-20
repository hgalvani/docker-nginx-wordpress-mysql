# docker-nginx-wordpress-mysql

Generic stack for running wordpress cms with mysql and nginx.

After clonning, create an .env file. Fill empty variables

>PROJECT_NAME=
>MYSQL_DBNAME=
>MYSQL_USER=
>MYSQL_PASSWORD=
>MYSQL_ROOT_PASSWORD=
>AWS_ACCESS_KEY_ID=
>AWS_SECRET_ACCESS_KEY=

Check config with
``docker-compose config``

Build stack with local DB
``docker-compose up -d``

Build stack in production env
``docker-compose up -d``

Display contenairs
``docker-compose ps``

               Name                             Command               State                 Ports
---------------------------------------------------------------------------------------------------------------
docker-nginx-wordpress-mysql_app_1   docker-entrypoint.sh php-fpm     Up      0.0.0.0:9000->9000/tcp
docker-nginx-wordpress-mysql_web_1   /docker-entrypoint.sh ngin ...   Up      0.0.0.0:80->80/tcp

## Clean stack

``docker-compose down -v  
sudo rm -rf ./data/* ./logs/*``
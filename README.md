# docker-nginx-wordpress-mysql

Generic stack for running wordpress cms with mysql and nginx.

After clonning, create an .env file. Fill empty variables

>PROJECT_NAME=
>MYSQL_DBNAME=$PROJECT_NAME
>MYSQL_USER=$PROJECT_NAME
>MYSQL_PASSWORD=
>MYSQL_ROOT_PASSWORD=
>AWS_ACCESS_KEY_ID=
>AWS_SECRET_ACCESS_KEY=

Check config with
``docker-compose config``

Build stack with local DB
``docker-compose -f docker-compose.yml -f docker-compose.local.yml up -d``

Build stack in production env
``docker-compose up -d``

### Backup DB

``source .env
docker exec $(docker ps | grep mysql | awk '{print $1}') /usr/bin/mysqldump -u root --password=<MYSQL_ROOT_PASSWORD> <MYSQL_DBNAME>> ./backup/<MYSQL_DBNAME>.sql``

### Clean stack

``docker-compose down -v  
sudo rm -rf ./data/* ./logs/*``

### Restore db

Add this line at then end of volumes declaration for db containers
``db:
        image: mysql:5.7
        ...
        volumes:
          ...
          - ./backup/<MYSQL_DBNAME>.sql:/docker-entrypoint-initdb.d/<MYSQL_DBNAME>sql``

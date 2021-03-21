# docker-nginx-wordpress-mysql

Generic stack for running nginx only

Check config with
`docker-compose config`

Build stack
`docker-compose up -d`

Display contenairs
`docker-compose ps`

```bash
      Name                    Command               State         Ports       
------------------------------------------------------------------------------
nginx-only_web_1   /docker-entrypoint.sh ngin ...   Up      0.0.0.0:80->80/tcp
```

## Clean stack

```bash
docker-compose down -v  
sudo rm -rf ./logs/*
```

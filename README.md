# Money Note Docker Running

This project is about how to run MoneyNote in Docker, support amd and arm.

#### Please be note if running in public network
1. The default mysql root password is 78p7gkc1, please change it after setup.
2. Please change the default invite code.

### Quick Run

```sh
docker run --name moneynote -e DB_PASSWORD=78p7gkc1 -e invite_code=111111 -v moneynote_mysql_data:/var/lib/mysql -p 43740:3306 -p 43741:80 -p 43742:9092 -p 43743:81 -p 43744:82 markliu2018/moneynote-all:latest
```

If you have mysql service, you can use docker image without mysql service.

```sh
docker run --name moneynote -d \
	-e DB_HOST=your_ip \
	-e DB_PORT=3306 \
	-e DB_NAME=moneynote \
	-e DB_USER=root \
    -e DB_PASSWORD=your_password \
	-e invite_code=111111 \
	-p 43742:9092 \
	-p 43743:81 \
	-p 43744:82 \
	markliu2018/moneynote-all-no-mysql:latest
```

### docker compose running（Recommended）

1. Fetch source code, use git.

```sh
git clone https://github.com/getmoneynote/docker-compose-moneynote-hub.git && cd docker-compose-moneynote-hub
```

2. docker compose running

```sh
docker compose up -d
```

3. Upgrade

```sh
docker compose pull && docker compose up -d
```

After Running, Visit PC Web [http://127.0.0.1:43743](http://127.0.0.1:43743)

Mobile H5, [http://127.0.0.1:43744](http://127.0.0.1:43744)。

phpMyAdmin [http://127.0.0.1:43741](http://127.0.0.1:43741) you can export data。

#### docker note

with mysql running (arm)
```sh
docker compose --env-file api.env -f docker-compose-hub.yml up -d
```

with mysql upgrade
```sh
docker compose --env-file api.env -f docker-compose-hub.yml pull && docker compose --env-file api.env -f docker-compose-hub.yml up -d
```

no mysql running
```sh
docker compose --env-file api-no-mysql.env -f docker-compose-hub-no-mysql.yml up -d
```

no mysql upgrade
```sh
docker compose --env-file api-no-mysql.env -f docker-compose-hub-no-mysql.yml pull && docker compose --env-file api-no-mysql.env -f docker-compose-hub-no-mysql.yml up -d
```

docker 5 in 1 running
```sh
docker compose --env-file api.env -f docker-compose-all-hub.yml up -d
```

docker 5 in 1 upgrade
```sh
docker compose -f docker-compose-all-hub.yml pull && docker compose --env-file api.env -f docker-compose-all-hub.yml up -d
```

docker 3 in 1 running
```sh
docker compose --env-file api-no-mysql.env -f docker-compose-all-no-mysql-hub.yml up -d
```

docker 3 in 1 upgrade
```sh
docker compose -f docker-compose-all-hub.yml pull && docker compose --env-file api-no-mysql.env -f docker-compose-all-no-mysql-hub.yml up -d
```
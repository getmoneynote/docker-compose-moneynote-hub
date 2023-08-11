# 九快记账个人部署方案

![Struct](https://raw.githubusercontent.com/getmoneynote/docker-compose-moneywhere/main/struct.png "Struct")

本项目提供docker compose一键运行九快记账，搭建自己的记账环境。

部署前，请确保已安装docker compose。如遇到任何问题欢迎加入 QQ群: 639653091 讨论。

部署步骤：
1. 请下载本项目源代码，使用git命令或直接下载源代码。

```sh
  $ git clone https://github.com/getmoneynote/docker-compose-moneywhere.git
```

2. 未保证数据安全问题，请修改数据库默认密码，一共3个地方需要修改。
    1. docker-compose.yml文件 MYSQL_ROOT_PASSWORD变量
   2. docker-compose.yml文件 healthcheck -p密码
   3. api.env DB_PASSWORD变量修改
3. 为防止恶意注册，请修改默认邀请码。api.env文件，invite_code变量修改
4. 执行命令

```sh
  $ docker compose up -d
```

如果docker hub镜像无法访问，请使用阿里云镜像：

```sh
  $ docker compose -f docker-compose-ali.yml up -d
```

版本升级，使用最新镜像。
```sh
  $ docker compose stop
  $ docker compose build --no-cache
  $ docker compose up -d
```

成功运行后，访问 [http://127.0.0.1:9097](http://127.0.0.1:9097) 可以打开网页版记账程序，使用前请注册一个账户，默认的邀请码是111111（6个1）, 为防止被恶意注册，请修改默认邀请码。

使用手机浏览器访问，[http://127.0.0.1:9098](http://127.0.0.1:9098) （127.0.0.1替换成你的地址）。

如需备份数据，请访问 [http://127.0.0.1:8085](http://127.0.0.1:8085) 打开phpMyAdmin操作，数据库是MySQL5.7。

phpMyAdmin登录的信息请对照api.env配置文件填写。请定期使用phpMyAdmin导出sql文件，备份你的记账数据！！！！！！！！

## QA
1. 很多人安装遇到数据库的问题，有可能是之前安装过，有数据文件，且自己修改过root密码。 使用 docker volume ls 命令查看有没有moneywhere_mysql_data文件，如果有，可以自己修改为另外的数据文件，或者删除moneywhere_mysql_data

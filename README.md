# 九快记账个人部署方案

本项目提供docker compose一键运行九快记账，搭建自己的记账环境。

请确保本机已安装docker compose。如遇到任何问题欢迎加入 QQ群: 639653091 讨论。

```sh
  $ git clone --depth 1 https://github.com/getmoneynote/docker-compose-moneywhere.git
  $ docker compose up
```
 如果遇到启动失败，将docker停止后，重新执行docker compose up。

 启动失败也可尝试 docker-compose -f docker-compose2.yml up

 版本升级，使用最新镜像。
 ```sh
  $ docker compose stop
  $ docker compose build --no-cache
  $ docker compose up -d
```

成功运行后，访问 [http://127.0.0.1:9097](http://127.0.0.1:9097) 可以打开网页版记账程序，使用前请注册一个账户，默认的邀请码是111111（6个1）。

如需备份数据，请访问 [http://127.0.0.1:8085](http://127.0.0.1:8085) 打开phpMyAdmin操作，数据库是MySQL5.7。

请定期使用打开phpMyAdmin导出sql文件，备份你的记账数据！！！！！！！！

邀请码可以在api.env文件修改 invite_code 变量，如遇端口冲突问题，请修改docker-compose.yml文件修改对应的端口。

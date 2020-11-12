# 服务启停

使用由Websoft9提供的 rethinkdb 部署方案，可能需要用到的服务如下：

## rethinkdb

```shell
sudo systemctl start rethinkdb-server
sudo systemctl stop rethinkdb-server
sudo systemctl restart rethinkdb-server
sudo systemctl status rethinkdb-server

# you can use this debug mode if rethinkdb service can't run
rethinkdb-server console
```

### MySQL

```shell
sudo systemctl start mysql
sudo systemctl stop mysql
sudo systemctl restart mysql
sudo systemctl status mysql
```

### Redis

```shell
systemctl start redis
systemctl stop redis
systemctl restart redis
systemctl status redis
```
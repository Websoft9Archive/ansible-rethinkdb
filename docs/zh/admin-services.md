# 服务启停

使用由 Websoft9 提供的 RethinkDB 部署方案，可能需要用到的服务如下：

### RethinkDB

```shell
sudo systemctl start rethinkdb
sudo systemctl stop rethinkdb
sudo systemctl restart rethinkdb
sudo systemctl status rethinkdb
```

### Nginx

```shell
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl status nginx
```
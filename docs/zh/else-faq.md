# FAQ

#### 是否有 RethinkDB 的 CLI 工具？

有，安装后存在cli命令，通过 `rethinkdb -h`查看使用详细

#### `rethinkdb repl` 命令如何采用密码登录？

```
rethinkdb repl --password-file /tmp/pw
```

其中 /tmp/pw 为存放密码明文的文件。

#### RethinkDB支持哪些语言？

我们提供Ruby，Python，Java和JavaScript / Node.js的官方驱动程序。社区支持的驱动程序支持十多种其他语言，包括C＃/。NET，Go和PHP。

#### 是否可通过命令行修改 RethinkDB 控制台密码？

可以，运行下面的命令即可：
```
htpasswd -b /etc/nginx/.htpasswd admin new_password
```

#### 是否可以通过 IP+端口的方式访问 RethinkDB？

不可以，为了安全考量默认仅支持 127.0.0.1 访问，所以需通过 Nginx 转发。

#### RethinkDB 控制台的账号密码是什么？

密码存放在服务器相关文件中：`/credentials/password.txt`

#### 是否有可视化的数据库管理工具？

有，访问地址：*http://服务器公网IP*

#### 是否可以修改rethinkdb的源码路径？

不可以

#### 如何修改上传的文件权限?

```shell
# 拥有者
chown -R nginx.nginx /data/rethinkdb/
# 读写执行权限
find /data/rethinkdb/ -type d -exec chmod 750 {} \;
find /data/rethinkdb/ -type f -exec chmod 640 {} \;
```

#### 部署和安装有什么区别？

部署是将一序列软件按照不同顺序，先后安装并配置到服务器的过程，是一个复杂的系统工程。  
安装是将单一的软件拷贝到服务器之后，启动安装向导完成初始化配置的过程。  
安装相对于部署来说更简单一些。 

#### 云平台是什么意思？

云平台指提供云计算服务的平台厂家，例如：Azure,AWS,阿里云,华为云,腾讯云等

#### 实例，云服务器，虚拟机，ECS，EC2，CVM，VM有什么区别？

没有区别，只是不同厂家所采用的专业术语，实际上都是云服务器
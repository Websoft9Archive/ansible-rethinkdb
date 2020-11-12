# RethinkDb

责任人：hzq

---

文档：[安装](https://rethinkdb.com/docs/install/ubuntu/)|[配置](https://rethinkdb.com/docs/start-on-startup/)

平台：Ubuntu | CentOS | Debian | macOs等数十种操作系统

## 概要

RethinkDB是第一个为实时Web从头开始构建的、开源的、可扩展的JSON数据库。
## 环境要求

- 程序语言：C++
- 服务器：Linux 32/64、Mac OS version > 10.7
- 客户端：支持其语言(Ruby、Python、Java、JavaScript/Node.js、C#/.NET、Go、Php等)的任何平台
- 服务器最小容量：RAM > 2GB
## 安装说明
官方提供包安装和源码安装两种方式，经过评估，这里使用包安装的方式。

1. 配置软件源
2. 使用包管理工具进行安装
3. 配置rethinkdb
4. 运行

<b>配置软件源</b>

centos7：
```shell
sudo cat << EOF > /etc/yum.repos.d/rethinkdb.repo
[rethinkdb]
name=RethinkDB
enabled=1
baseurl=https://download.rethinkdb.com/repository/centos/7/x86_64/
gpgkey=https://download.rethinkdb.com/repository/raw/pubkey.gpg
gpgcheck=1
EOF
sudo yum update -y
```
Ubuntu:
```shell

source /etc/lsb-release && echo "deb https://download.rethinkdb.com/repository/ubuntu-$DISTRIB_CODENAME $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/rethinkdb.list
wget -qO- https://download.rethinkdb.com/repository/raw/pubkey.gpg | sudo apt-key add -

sudo apt-get update -y

```
<b>安装</b>

Centos 7:

 yum install rethinkdb -y

Ubuntu:

sudo apt-get install rethinkdb -y

<b>创建rethinkdb的数据目录</b>

```shell
sudo mkdir -p /data/rethinkdb/rethinkdb_data

rethinkdb create -d /data/rethinkdb/rethinkdb_data

sudo chown -R rethinkdb.rethinkdb /data/rethinkdb/rethinkdb_data
# 创建配置文件并进行配置
sudo cp /etc/rethinkdb/default.conf.sample /etc/rethinkdb/instances.d/instance.conf

sudo vim /etc/rethinkdb/instances.d/instance.conf
#需要更改directory=配置文件中的行以指向RethinkDB数据目录
#directory=/data/rethinkdb/rethinkdb_data
sed -i 32a\directory=/data/rethinkdb/rethinkdb_data /etc/rethinkdb/instances.d/instance.conf
```
<b>systemd设置启动</b>
1. 创建/usr/lib/tmpfiles.d/rethinkdb.conf包含以下内容的文件：
```shell
touch /usr/lib/tmpfiles.d/rethinkdb.conf
sudo sh -c  "echo 'd /run/rethinkdb 0755 rethinkdb rethinkdb -' > /usr/lib/tmpfiles.d/rethinkdb.conf"
```
2. 并创建服务文件/usr/lib/systemd/system/rethinkdb.service：

```sh
sudo mkdir -p /usr/lib/systemd/system
sudo touch /usr/lib/systemd/system/rethinkdb.service
sudo echo "[Unit]
Description=RethinkDB database server for instance 
[Service]
User=rethinkdb
Group=rethinkdb
ExecStart=/usr/bin/rethinkdb serve --config-file /etc/rethinkdb/instances.d/instance.conf
KillMode=process
PrivateTmp=true

[Install]
WantedBy=multi-user.target" > /usr/lib/systemd/system/rethinkdb.service

sudo chmod 644 /usr/lib/tmpfiles.d/rethinkdb.conf /usr/lib/systemd/system/rethinkdb.service 
#***sudo systemctl enable rethinkdb
```
#设置开机启动

sudo systemctl daemon-reload

sudo systemctl enable rethinkdb

sudo systemctl start rethinkdb
```


安装时候遇到问题:
-  Error: Package: rethinkdb-2.4.1-30488.x86_64(rethinkdb)
        Requires: glibc >=2.28
        Install: glibc-2,17-307.e17.1.x86_64(@base)

    解决方案：更换对应版本的软件源可以解决（问题是安装了不匹配的仓库和包）
    yum clean all
    yum update -y
# 重新安装
sudo yum install rethinkdb -y





## 路径
日志路径:   /data/rethinkdb/rethinkdb_data/log_file

配置文件：  /etc/rethinkdb/instances.d/instance.conf

数据路径:   /data/rethinkdb/rethinkdb_data

程序路径：  /usr/bin/rethinkdb
## 配置
    sudo cp /etc/rethinkdb/default.conf.sample /etc/rethinkdb/instances.d/instance.conf
    sudo vim /etc/rethinkdb/instances.d/instance.conf
配置文件：[配置文件支持的选项](https://rethinkdb.com/docs/config-file/)
## 账号密码

<p>一个新的RethinkDB群集始终有一个名为的用户admin；该用户始终在全局范围内拥有所有权限，并且无法删除该用户。默认情况下，admin用户没有密码。您可以通过更新admin用户文档或在启动时指定--initial-password 命令行选项来更改此设置。如果以前没有设置用户密码，请设置该密码；用于auto选择要打印到的随机密码stdout</p>

Web管理UI始终像admin用户一样进行连接，`并跳过身份验证过程（即，该连接未使用密码）`。虽然无法对Web UI进行密码保护，但可以使用--bind-http命令行选项限制它接受连接的地址。
## 服务
无
## 环境变量
无
## 版本号
```shell
sudo sh -c "rethinkdb --version >> /data/rethinkdb/rethinkdb_install_version.txt"
cat /data/rethinkdb/rethinkdb_install_version.txt
```
## 常见问题

<b>有没有管理控制台?</b>

有，通过[http://公网IP:8080]()访问

本项目需要开启哪些端口?
|item|port|
|-----------|----|
|侦听集群|29015|
|侦听客户|28015|
|侦听http管理|8080|


<br >

-  请注意，默认情况下，RethinkDB仅打开绑定到的连接 `localhost`，以防止网络上未经授权的客户端连接到服务器。用`rethinkdb --bind all`选项允许从网络上的任何地方进行连接。如果网络受到保护，它将很好地工作。

-  看到“收到无效的群集标题”消息？ RethinkDB使用三个端口进行操作-HTTP Web UI端口，客户端驱动程序端口和集群内流量端口。您可以将浏览器连接到Web UI端口以直接从浏览器管理群集，并将客户端驱动程序连接到客户端驱动程序端口以从应用程序运行查询。如果您正在运行群集，则不同的RethinkDB节点将通过群集内流量端口相互通信。

- 该消息received invalid clustering header表示存在端口不匹配，并且某些东西连接到错误的端口。例如，如果不小心指向浏览器或将客户端驱动程序连接到群集内流量端口，则通常会收到此消息。
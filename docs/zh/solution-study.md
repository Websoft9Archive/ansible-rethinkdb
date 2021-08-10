# 知识点


## 概要

RethinkDB 是一个与 MongoDB 对标的开源数据库，RethinkDB 定位于实时数据库应用：

- 协作式Web和移动应用程序
- 流分析应用
- 多人游戏
- 实时市场
- 连接的设备

## 用户权限

RethinkDB 中的用户类似于大多数其他数据库系统中的用户。  

### 用户管理

#### 管理密码

默认管理员用户名为 `admin`，密码为空。通过服务端命令行，可以很方便的设置管理员密码：

```
rethinkdb --initial-password yourpassword
```

#### 创建用户

RethinkDB 不仅仅支持管理员用户，用户也可以增加更多的用户，所有的用户信息存储在 **users** [系统表](https://rethinkdb.com/docs/system-tables/)中。  

由于系统表只有 admin 用户采用访问权限，因此必须以 admin 用户连接到数据库之后，再参考下面命令创建新用户：  

```
# 创建带密码的用户
r.db('rethinkdb').table('users').insert({id: 'username', password: 'secret'})
```

#### 重置密码

```
# 重置为新密码
r.db('rethinkdb').table('users').get('username').update({password: newpassword})

# 重置为空密码
r.db('rethinkdb').table('users').get('username').update({password: false})
```

### 权限

权限存储在 permissions 系统表中。虽然您可以通过修改该表中的文档来更改权限，但使用grant命令要方便得多。

默认支持四种权限：

* read
* write
* config
* connect

有三种权限范围：  

* 表（仅影响表）
* 数据库（影响数据库和其中的表）
* 全局（影响所有数据库和其中的表）


## 访问控制

RethinkDB 默认启动不支持远程访问，修改它的配置文件：*/etc/rethinkdb/instances.d/instance.conf*  中的 bind 项。  
```
bind=0.0.0.0
```


## 数据

### 系统表

RethinkDB 维护特殊的[系统表](https://rethinkdb.com/docs/system-tables/)，其中包含有关服务器、数据库、单个表和集群问题的配置和状态信息。

### 备份

运行 `rethinkdb dump` 备份数据

### 导入

运行 `rethinkdb import` 导入数据

## 集群


## ReQL

RethinkDB 不支持传统是数据库语言 SQL 。但是，RethinkDB的查询语言 [ReQL](https://rethinkdb.com/docs/introduction-to-reql/) 几乎可以执行 SQL 所能做的一切，包括表联接和聚合功能，并且功能强大，表达力强且易于学习。  

ReQL还可以完成SQL无法完成的许多工作，包括将查询与JavaScript表达式和map-reduce混合使用。

# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 域名绑定

当服务器上只有一个网站时，不做域名绑定也可以访问网站。但从安全和维护考量，**域名绑定**不可省却。

以示例网站为例，域名绑定操作步骤如下：

1. 确保域名解析已经生效  

2. 使用 SFTP 工具登录云服务器

3. 修改 [Nginx虚拟机主机配置文件](/zh/stack-components.md#nginx)，将其中的 **server_name** 项的值修改为你的域名
   ```text
   server
   {
    listen 80;
    server_name example.yourdomain.com; # 此处修改为真实域名
    location / {
        proxy_pass  http://127.0.0.1:8080; 
   ...
   }
   ```
4. 保存配置文件，重启 [Nginx 服务](/zh/admin-services.md#nginx)

## 控制台密码

本部署方案通过 Nginx 验证访问控制 RethinkDB 的访问，通过如下两个步骤修改密码：

1. 编辑 Nginx 验证访问控制文件： */etc/nginx/.htpasswd/htpasswd.conf* 中的密码
2. 重启 Nginx 服务后生效
   ```
   sudo systemctl restart nginx
   ```

## 远程访问

RethinkDB 远程访问的开关存储在：*/etc/rethinkdb/instances.d/instance.conf* 文件中。  

只需执行下面命令，然后重启服务，即可开启远程访问。

```
sudo sed -n "s/^#bind=/bind=0.0.0.0/g" /etc/rethinkdb/instances.d/instance.conf
```

## 用户管理

下面以 Python 客户端新增一个用户并设置其初始密码作为范例进行说明

1. 以 `admin` 用户身份连接数据库
   ```
   from rethinkdb import r

   # 无密码连接
   r.connect('localhost', 28015).repl()

   # 有密码连接
   r.connect('localhost', 28015, password='123456').repl()
   ```

2. 新增用户名和密码
   ```
   r.db('rethinkdb').table('users').insert({id: 'bob', password: 'secret'})
   ```

## 重置密码

常用的 RethinkDB 重置密码相关的操作主要有修改密码和清空密码（将密码设置为空）两种方式。  

1. 登录 RethinkDB Web 界面，在【Data explorer】下输入所需的命令

   ```
   # 修改密码命令
   r.db('rethinkdb').table('users').get('admin').update({password: 'newpassword'})

   # 清空密码命令
   r.db('rethinkdb').table('users').get('admin').update({password: false})
   ```
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rethinkdb/rethinkdb-editpassword-websoft9.png)

2. 点击【run】后生效
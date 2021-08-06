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

只需加入如下的配置段，然后重启服务，即可开启远程访问。

```
bind=0.0.0.0
```
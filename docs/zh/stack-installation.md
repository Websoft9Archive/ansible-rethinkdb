# 初始化安装

在云服务器上部署 RethinkDB 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:80** 端口是否开启
3. 若想用域名访问 RethinkDB **域名控制台** 完成一个域名解析

## RethinkDB 安装向导

1. 使用本地电脑的浏览器访问网址：*http://域名* 或 *http://服务器公网IP*，准备登陆 RethinkDB 控制台

2. 输入用户名和密码（[不知道账号密码？](/zh/stack-accounts.md#rethinkdb)）

3. 成功登录到 RethinkDB 后台  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rethinkdb/rethinkdb-gui-websoft9.png)

## RethinkDB 入门向导

下面通过 RethinkDB 控制台，演示如何增加 Database 和 Table：

1. 依次打开：【Tables】>【Add Database】，增加一个数据库
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rethinkdb/rethinkdb-adddb-websoft9.png)

2. 打开数据库，点击【Add Table】增加表
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rethinkdb/rethinkdb-addtable-websoft9.png)

> 需要了解更多 RethinkDB 的使用，请参考官方文档：[RethinkDB Documentation](https://rethinkdb.com/docs)

## 常见问题

#### 浏览器打开IP地址，无法访问 RethinkDB（白屏没有结果）？

您的服务器对应的安全组80端口没有开启（入规则），导致浏览器无法访问到服务器的任何内容

#### RethinkDB 控制台运行在哪个端口？

8080 端口，本部署方案通过 Nginx 转发到了 80 端口。
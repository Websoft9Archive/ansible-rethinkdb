# FAQ

#### If there have RethinkDB CLI?

Yes, `rethinkdb -h` for CLI help

#### Is there a web-base GUI database management tools?

Yes, visit by *http://Server's Internet IP*

#### Can I visit RethinkDB web console by *http://IP:8080*?

No, RethinkDB web console now allow visit from 127.0.0.1

#### What is the password for the database root user?

The password is stored in the server related file: `/credentials/password.txt`

#### Is it possible to modify the source path of rethinkdb?

No

#### How to change the permissions of filesytem?

Change owner(group) or permissions like below:

```shell
chown -R nginx.nginx /data/rethinkdb
find /data/rethinkdb -type d -exec chmod 750 {} \;
find /data/rethinkdb -type f -exec chmod 640 {} \;
```

#### What's the difference between Deployment and Installation?

- Deployment is a process of installing and configuring a sequence of software in sequence in a different order, which is a complex system engineering.  
- Installation is the process of starting the initial wizard after the application is prepared.  
- Installation is simpler than deployment. 

#### What's Cloud Platform?

Cloud platform refers to platform manufacturers that provide cloud computing services, such as: **Azure, AWS, Alibaba Cloud, HUAWEI CLOUD, Tencent Cloud**, etc.

#### What is the difference between Instance, Cloud Server, Virtual Machine, ECS, EC2, CVM, and VM?

No difference, just the terminology used by different manufacturers, actually cloud servers
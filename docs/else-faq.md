# FAQ

#### When is RethinkDB a good choice?

RethinkDB is a great choice when your applications could benefit from realtime feeds to your data.

The query-response database access model works well on the web because it maps directly to HTTP’s request-response. However, modern applications require sending data directly to the client in realtime. Use cases where companies benefited from RethinkDB’s realtime push architecture include:

- Collaborative web and mobile apps
- Streaming analytics apps
- Multiplayer games
- Realtime marketplaces
- Connected devices
- For example, when a user changes the position of a button in a collaborative design app, the server has to notify other users that are simultaneously working on the same project. Web browsers support these use cases via WebSockets and long-lived HTTP connections, but adapting database systems to realtime needs still presents a huge engineering challenge.

RethinkDB is the first open-source, scalable database designed specifically to push data to applications in realtime. It dramatically reduces the time and effort necessary to build scalable realtime apps.


#### Who is using RethinkDB in production?

RethinkDB is being used in production by hundreds of technology startups, consulting studios, and Fortune 500 companies. Here are some example use cases:

- Jive Software and Mediafly use RethinkDB to power reactive web and mobile apps
- Pristine.io and Narrative Clip use RethinkDB to power cloud infrastructure for connected devices
- Platzi and Workshape.io use RethinkDB to power realtime analytics
- NodeCraft and GameServerKings use RethinkDB to power massively scalable multiplayer games
- RethinkDB has a vibrant community of over 100,000 developers, and hundreds of contributors from around the world.


#### How is RethinkDB different from MongoDB?

RethinkDB is based on a fundamentally different architecture from MongoDB. Instead of polling for changes, the developer can tell RethinkDB to continuously push updated query results in realtime. You can also write applications on top of RethinkDB using traditional query-response paradigm, and subscribe to realtime feeds later as you start adding realtime functionality to your app.

#### What languages can I use to work with RethinkDB?

We provide official drivers for Ruby, Python, Java, and JavaScript/Node.js. Community-supported drivers exist for more than a dozen other languages, including C#/.NET, Go, and PHP.

#### Does RethinkDB support SQL?

No. However, RethinkDB’s query language can do nearly anything SQL can do, including table joins and aggregation functions, and it’s powerful, expressive and easy to learn. ReQL can also do many things SQL can’t do, including mixing queries with JavaScript expressions and map-reduce.

#### Are RethinkDB transactions atomic?

Most write operations involving a single document in RethinkDB are guaranteed to be atomic. Operations that are not deterministic cannot update documents in an atomic fashion (such as random values, or values obtained as the result of a subquery). In addition, multiple documents are not updated atomically.

#### If there is no domain name, can I deploy rethinkdb?

Yes, visit rethinkdb by *http://Internet IP:28015*

#### What is the password for the database root user?

The password is stored in the server related file: `/credentials/password.txt`

#### Is there a web-base GUI database management tools?

Yes, visit by *http://Internet IP:8080*

#### Is it possible to modify the source path of rethinkdb?

No

#### How to change the permissions of filesytem?

Change owner(group) or permissions like below:

```shell
chown -R apache.apache /data/wwwroot
find /data/wwwroot -type d -exec chmod 750 {} \;
find /data/wwwroot -type f -exec chmod 640 {} \;
```

#### What's the difference between Deployment and Installation?

- Deployment is a process of installing and configuring a sequence of software in sequence in a different order, which is a complex system engineering.  
- Installation is the process of starting the initial wizard after the application is prepared.  
- Installation is simpler than deployment. 

#### What's Cloud Platform?

Cloud platform refers to platform manufacturers that provide cloud computing services, such as: **Azure, AWS, Alibaba Cloud, HUAWEI CLOUD, Tencent Cloud**, etc.

#### What is the difference between Instance, Cloud Server, Virtual Machine, ECS, EC2, CVM, and VM?

No difference, just the terminology used by different manufacturers, actually cloud servers
# Initial Installation

If you have completed the RethinkDB deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure the TCP:80 is allowed
3. Make a domain resolution on your DNS Console if you want to use domain for rethinkdb

## RethinkDB Verify Wizard

1. Using local browser to visit the RethinkDB login page URL *http://DNS* or *http://Server's Internet IP* 

2. Input the username and password ([Don't have password?](/stack-accounts.md#rethinkdb))  

3. You can see the interface of RethinkDB
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/rethinkdb/rethinkdb-gui-websoft9.png)

## RethinkDB Setup Wizard

These steps will show you how to create Database and Table by RethinkDB console:

1. Open: 【Tables】>【Add Database】to create a database
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/rethinkdb/rethinkdb-adddb-websoft9.png)

2. Click this the database you added and click 【Add Table】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/rethinkdb/rethinkdb-addtable-websoft9.png)

> More useful RethinkDB guide, please refer to [RethinkDB Documentation](https://rethinkdb.com/docs)

## Q&A

#### I can't visit the start page of RethinkDB?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### Which port used for RethinkDB console？

8080 port, this deployment solution use Nginx proxy to 80 port
# Troubleshooting

We collect the most common troubleshooting of using rethinkdb for your reference:

> Instance troubleshooting is closely related to the Instance provider that is Cloud Platform, refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs directory: `/data/logs`

#### I get a “ReqlResourceLimitError: Array over size limit 100000” when trying to order a table

Ordering without an index requires the server to load the whole sequence in an array, which is limited by default to 100,000 documents. You can use the arrayLimit option to run to temporarily raise this limit. However, a more efficient option is to use an index. See the documentation for orderBy for more information.

#### My insert queries are slow. How can I speed them up?
RethinkDB uses a safe default configuration for write acknowledgement. Each write is committed to disk before the server acknowledges it to the client. If you’re running a single thread that inserts documents into RethinkDB in a loop, each insert must wait for the server acknowledgement before proceeding to the next one. This can significantly slow down the overall throughput.
This behavior is similar to any other safe database system. Below is a number of steps you can take to speed up insert performance in RethinkDB. Most of these guidelines will also apply to other database systems.
Increase concurrency. Instead of having a single thread inserting data in a loop, create multiple threads with multiple connections. This will allow parallelization of insert queries without spending most of the time waiting on disk acknowledgement.
Batch writes. Instead of doing single writes in a loop, group writes together. This can result in significant increases in throughput.
Consider using soft durability mode. 
Consider using noreply mode. 

#### Which versions of Node.js are supported?

The JavaScript driver currently works with Node.js versions 0.10.0 and above. You can check your node version as follows:
node --version

#### rethinkdb service can't start?

1. Use the debug mode of `systemctl status rethinkdb` and you can see the errors

2. Search the keywords **Failed** or **error** from logs: */data/logs/rethinkdb-server*

#### Error in Chrome when modify password?

This error is not attribute to rethinkdb server, once you have upgraded you local Chrome, it solved

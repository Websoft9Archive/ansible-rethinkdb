# Knowledge

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

#### I get a “ReqlResourceLimitError: Array over size limit 100000” when trying to order a table

Ordering without an index requires the server to load the whole sequence in an array, which is limited by default to 100,000 documents. You can use the arrayLimit option to run to temporarily raise this limit. However, a more efficient option is to use an index. See the documentation for orderBy for more information.

#### My insert queries are slow. How can I speed them up?
RethinkDB uses a safe default configuration for write acknowledgement. Each write is committed to disk before the server acknowledges it to the client. If you’re running a single thread that inserts documents into RethinkDB in a loop, each insert must wait for the server acknowledgement before proceeding to the next one. This can significantly slow down the overall throughput.
This behavior is similar to any other safe database system. Below is a number of steps you can take to speed up insert performance in RethinkDB. Most of these guidelines will also apply to other database systems.
Increase concurrency. Instead of having a single thread inserting data in a loop, create multiple threads with multiple connections. This will allow parallelization of insert queries without spending most of the time waiting on disk acknowledgement.
Batch writes. Instead of doing single writes in a loop, group writes together. This can result in significant increases in throughput.
Consider using soft durability mode. 
Consider using noreply mode. 
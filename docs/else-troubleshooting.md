# Troubleshooting

We collect the most common troubleshooting of using rethinkdb for your reference:

> Instance troubleshooting is closely related to the Instance provider that is Cloud Platform, refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs directory: `/data/logs`

#### RethinkDB service can't start?

1. Use the debug mode of `sudo systemctl status rethinkdb` and you can see the errors

2. Search the keywords **Failed** or **error** from logs: */data/logs/rethinkdb-server*

#### Error in Chrome when modify RethinkDB password?

You should clear Chrome cache or open incognito tab to access RethinkDB

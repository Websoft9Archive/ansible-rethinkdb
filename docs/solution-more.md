# More

Each of the following solutions has been proven to be effective and we hope to be helpful to you.

## Domain binding

The precondition for binding a domain is that rethinkdb can accessed by domain name.

Nonetheless, from the perspective of server security and subsequent maintenance considerations, the **Domain Binding** step cannot be omitted.

rethinkdb domain name binding steps:

1. Connect your Cloud Server
2. Modify [Nginx vhost configuration file](/stack-components.md#nginx), change the **server_name**'s value to your domain name
   ```text
   server
   {
    listen 80;
    server_name example.yourdomain.com; # set your DNS here
    location / {
        proxy_pass  http://127.0.0.1:8080; 
   ...
   }
   ```

## Reset RethinkDB console password

Run `htpasswd -b /etc/nginx/.htpasswd admin new_password` command to reset password
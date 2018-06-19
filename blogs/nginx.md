---
Date: May 25, 2018
Topic: Nginx
---

# Use Nginx as a Reverse Proxy

## Configuration on Mofii.NET

> First let Apache2 listen to port 81 instead of 80.

1. Mofidy **/etc/apache2/ports.conf**:

   `Listen 80` to `Listen 81`

2. Modify **/etc/apache2/sites-enabled/twitter.conf**:

   `<VirtualHost: *:80>` to `<VirtualHost: *:81>`

3. Modify **/etc/apache2/sites-enabled/FlaskApp.conf**:

   `<VirtualHost: *:80>` to `<VirtualHost: *:81>`

4. Modify **/etc/apache2/ports.conf**:

   `<VirtualHost: *:80>` to `<VirtualHost: *:81>`

> Install and let Nginx listen to port 80. Now we can use `sudo service nginx start` to start nginx server.

5. Modify **/etc/nginx/sites-enabled/default** to enable reverse proxy:

   ```
   server_name mofii.net;

   location / {
       proxy_pass https://www.google.com;
   }
   ```

6. After configuration, use `nginx -c /etc/nginx/nginx.conf -t` to test nginx.

7. If syntax is `ok` and test is `successful`, use `sudo service nginx start` to start server.

## Final Thoughts

I tried to implement reverse proxy to enable Twitter widgets behind the GFW. It seems that this method fails when it comes to iframe. Passing google.com works fine but passing Twitter blogs still fails.

P.S. I should have seen this coming lol

## Related Links

* Nginx Reverse Proxy on Apache2: https://www.howtoing.com/how-to-set-nginx-as-a-reverse-proxy-for-apache2-on-ubuntu-12.04

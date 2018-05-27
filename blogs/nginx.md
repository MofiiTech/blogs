---
Date: May 25, 2018
Topic: Nginx
---

# Use Nginx as a Reverse Proxy

## Steps

1. Modify **/etc/apache2/ports.conf**:

   `Listen 80` to `Listen 8000`

2. Modify **/etc/apache2/sites-enabled/twitter.conf**:

   `<VirtualHost *:80>` to `<VirtualHost 127.0.0.1:8000>`

3. Modify **/etc/apache2/apache2.conf**:

   `LogFormat "%h %l %u %t \"%r\" %>s %b \"{Referer}i\" \"%{User-Agent}i\"" combined`

   to

   `LogFormat "%{X-Forwarded-For}i %l %u %t \"%r\" %>s %b \"{Referer}i\" \"%{User-Agent}i\"" combined`

## Related Links

* Nginx Reverse Proxy on Apache2: https://www.howtoing.com/how-to-set-nginx-as-a-reverse-proxy-for-apache2-on-ubuntu-12.04

## Configuration on Mofii.NET

> First let Apache2 listen to port 81 instead of 80.

1. Modify **/etc/apache2/sites-enabled/twitter.conf**:

   `<VirtualHost: *:80>` to `<VirtualHost: *:81>`

2. Modify **/etc/apache2/sites-enabled/FlaskApp.conf**:

   `<VirtualHost: *:80>` to `<VirtualHost: *:81>`

3. Modify **/etc/apache2/ports.conf**:

   `<VirtualHost: *:80>` to `<VirtualHost: *:81>`

> Install and let Nginx listen to port 80. Now we can use `sudo service nginx start` to start nginx server.

4. 

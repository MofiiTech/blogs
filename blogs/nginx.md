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

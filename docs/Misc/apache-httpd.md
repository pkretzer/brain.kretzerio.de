---
tags:
    - httpd
    - apache
    - rewrite
---

# Apache/httpd
## Rewrite http domain
With the below configuration file you can rewrite a domain call to another domain.
```apache
RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} ^domain-old\.de$ [NC]
RewriteRule ^(.*)$ http://domain-new.de [R=301,L]
```

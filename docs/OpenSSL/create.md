---
tags:
    - openssl
    - pem
    - key
    - certificate
    - selfsigned
---

# Create
## Create a selfsigned certificate with key
With the below command a selfsigned certificate and key without password will be created. If you want to have a password protected key remove **nodes**.
```bash
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
```

## Create dhparams
The below command create a dhparams file with 4096bit, be careful when setting higher values as it increased the time for creating significantly.
```bash
openssl dhparam -out /etc/ssl/dhparams.pem 4096
```

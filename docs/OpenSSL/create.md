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

## Create a selfsigned certificate with key and Subject AltName
With the below command a selfsigned certificate with Subject AltName and key without password will be created. If you want to have a password protected key remove **nodes**.
```bash
openssl req -x509 -newkey rsa:4096 -sha256 -days 365 -nodes -keyout key.pem -out cert.pem -subj "/CN=example.com" -addext "subjectAltName=DNS:example.com,IP:10.0.0.1"
```

## Create dhparams
The below command create a dhparams file with 4096bit, be careful when setting higher values as it increased the time for creating significantly.
```bash
openssl dhparam -out /etc/ssl/dhparams.pem 4096
```

## Create a CSR (Certificate Signing Request) with one line
```bash
openssl req -new -nodes -sha256 -newkey rsa:4096 -keyout example.com.key -out example.com.csr -subj "/emailAddress=domain@example.com/C=Country/ST=State/L=Location/O=Organization/CN=example.com" -addext "keyUsage=keyEncipherment, dataEncipherment" -addext "extendedKeyUsage=serverAuth" -addext "subjectAltName=DNS:example.com,*.example.com"
```

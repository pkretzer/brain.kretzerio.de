---
tags:
    - openssl
    - pfx
    - pkcs12
    - pem
    - key
    - certificate
    - convert
    - crt
    - cert
---

# Convert
## Create .p12 from pem
```bash
openssl pkcs12 -export -out file.p12 -inkey file.key -in file.pem
```

## .crt to .pem
```bash
openssl x509 -in mycert.crt -out mycert.pem -outform PEM
```

## .cert to .pem
```bash
openssl x509 -inform der -in mycert.cer -out mycert.pem -outform PEM
```

## .cert/.crt to .pfx
```bash
openssl pkcs12 -inkey my.key -in my.crt  -name myname -certfile ca-cert.pem -export -out my.pfx
```

## .pfx to .pem
The below command first creates a private key file from the pfx without a password. If you want the key password protected remove the **-nodes** option.
The seccond command creates the certificate file in pem format.
```bash
openssl pkcs12 -in my.pfx -nocerts -out my.key -nodes
openssl pkcs12 -in my.pfx -clcerts -nokeys -out my.pem
```

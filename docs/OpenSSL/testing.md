---
tags:
    - openssl
    - certificate
    - testing
---

# Testing
## Test SMTP with StartTLS via openssl
```bash
openssl s_client -starttls smtp -connect host.de:25
```

## Test SMTP via openssl
```bash
openssl s_client smtp -connect host.de:465
```

## Check certificate from domain
```bash
openssl s_client -showcerts -connect mydomain.de:443
```

## Check which TLS version is used for SMTP
With the below command you can try to connect to a mailserver with a specific tls protocol.
Possible values are:
- tls1  
- tls1_1  
- tls1_2  
- tls1_3  
```bash
openssl s_client -connect myawesomeserver.de:587 -starttls smtp -tls1_2
```

## Show certificate information
```bash
openssl x509 -in my.pem -text
```

## Show expiry or start date of certificate
**Domain**
```bash
openssl s_client -connect mydomain.de:443 | openssl x509 -noout -enddate
```

**File**
```bash
openssl pkcs12 -in my.p12 | openssl x509 -noout -enddate
```

**SMTP**
```bash
openssl s_client -connect 1.1.1.1:25 -starttls smtp | openssl x509 -noout -enddate
```

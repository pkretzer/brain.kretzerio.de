---
tags:
    - certificate-authority
    - ca
    - certificate
---

# Certificate Authority
## Sign CSR with Windows CA
```cmd
certreq -submit -attrib "CertificateTemplate:Webserver" example.com.csr example.com.crt
```

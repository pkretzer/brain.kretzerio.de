---
tags:
    - certbot
---

# Certbot
## Auto renewal cronjob
The below command tries to create a new let's encrypt certificate at 0 and 12 but waits a random time between 0 and 3600 seconds so the let's encrypt servers get not stressed with  
too many requests.
```bash
echo "0 0,12 * * * root python3 -c 'import random; import time; time.sleep(random.random() * 3600)' && certbot renew -q" >> /etc/crontab
```

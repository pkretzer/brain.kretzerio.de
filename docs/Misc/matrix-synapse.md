---
tags:
    - matrix-synapse
    - password
    - user
---

# Matrix-Synapse
## Create new user
Create new matrix-synapse user on the local system. Change the homeserver.yaml and address to your environment
```bash
register_new_matrix_user -c /etc/matrix-synapse/homeserver.yaml http://localhost:8008
```

## Change user password via api
Change the Bearer and Port to your environment and the user where you want to chance the password.
```bash
curl --header "Authorization: Bearer xxx" -X POST http://localhost:8008/_synapse/admin/v1/reset_password/@myuser:myserver.de -H "Content-Type: application/json" -d '{"new_password": "XXX"}'
```

## Show user data via api
Change the Bearer and Port to your environment and the user from which you want to get the informations.
```bash
curl --header "Authorization: Bearer xxx" -X GET http://localhost:8008/_synapse/admin/v1/whois/@myuser:myserver.de
```

```bash
curl --header "Authorization: Bearer xxx" -X GET http://localhost:8008/_matrix/client/r0/admin/whois/@myuser:myserver.de
```

## Deactivate user account
The below command removes the usr account GDPR compliant.
```bash
curl --header "Authorization: Bearer xxx" -X POST http://localhost:8008/_synapse/admin/v1/deactivate/@myuser:myserver.de -H "Content-Type: application/json" -d '{"erase": true}'
```

## Reactivate user account
The below command reactivates the user account and sets a new password so that the user can login.
```bash
curl --header "Authorization: Bearer xxx" -X PUT http://localhost:8008/_synapse/admin/v2/users/@myuser:myserver.de -H "Content-Type: application/json" -d '{"deactivated": false, "password": "supersecretpw"}'
```

---
tags:
    - vmware
    - broadcom
    - sql
    - user
---

# Horizon
## Show login times of user from SQL-Server database
With the below command you can check the login times from a specific user.
```sql
SELECT [ModuleAndEventText]
      ,[Time]
  FROM [myhorizondatabase].[dbo].[event]
  WHERE [ModuleAndEventText] LIKE '%my.user has logged%'
  ORDER BY [Time] DESC;
```

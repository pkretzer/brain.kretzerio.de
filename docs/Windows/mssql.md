---
tags:
    - microsoft
    - windows
    - mssql
    - ssms
---

# MSSQL
## Show active session ids
~~~sql
SELECT 
    session_id,
    login_name,
    host_name,
    program_name,
    status,
    last_request_start_time
FROM sys.dm_exec_sessions;
~~~

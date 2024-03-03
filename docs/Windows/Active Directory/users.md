---
tags:
    - microsoft
    - windows
    - active directory
---

# Users
## 
Export all Active Directory Users with group membership and e-mail address to a CSV file.
```powershell
Get-ADGroup -Filter * -PipelineVariable group | Get-ADGroupMember -Recursive | Get-ADUser -Properties EMailAddress -EA SilentlyContinue | %{[pscustomobject]@{'Gruppe' =$group.Name;'Mitglied' = $_.Name;'E-Mail' = $_.EMailAddress}} | sort Gruppe | export-csv "$env:Userprofile\Desktop\groupmembers.csv" -Delimiter ";" -NoType -Encoding UTF8
```

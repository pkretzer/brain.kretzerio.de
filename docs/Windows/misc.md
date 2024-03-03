---
tags:
    - microsoft
    - windows
    - certificate
    - planned task
    - deleting
---

# Misc
## Create selfsigned certificate via powershell
With the below command you can create a selfsigned certificate that is valid for 10 years from now on and put it in your "My Certificate" Trust Store.
You need to copy the certificate to Trusted Root CAs, otherwise it will not be valid for example for LDAPs.
```powershell
New-SelfSignedCertificate -FriendlyName "My selfsigned certificate" -DnsName srv1, srv1.domain.local -CertStoreLocation Cert:\LocalMachine\My -NotAfter (Get-Date).AddYears(10) -TextExtension @("2.5.29.37={text}1.3.6.1.5.5.7.3.1")
```

## Folder can't be deleted in explorer
Sometimes you have copied a folder or file from another storage with special characters that can't be displayed in windows explorer.  
Windows explorer can't delete those folders and you need to remove it via cli.
```cmd
rd "\\?\C:\folder\mybuggyfolder"
```

## Show filesystem blocksize
```cmd
fsutil fsinfo ntfsinfo c:
```

## Check if planned task exists and create one if not or update
**Current User**
```powershell
$restart_time = "23:03"
$existing_task = schtasks /query | Select-String "VMware-Tools-Upgrade-Restart"
    if ($existing_task -eq $null) {
        schtasks /create /sc once /tn "VMware-Tools-Upgrade-Restart" /tr "shutdown -r" /st $restart_time
    }
    else {
        schtasks /delete /tn "VMware-Tools-Upgrade-Restart" /f
        schtasks /create /sc once /tn "VMware-Tools-Upgrade-Restart" /tr "shutdown -r" /st $restart_time
    }
```

**System User**
```powershell
$restart_time = "23:03"
$existing_task = schtasks /query | Select-String "VMware-Tools-Upgrade-Restart"
    if ($existing_task -eq $null) {
        schtasks /create /sc once /tn "VMware-Tools-Upgrade-Restart" /tr "shutdown -r" /st $restart_time /ru "SYSTEM"
    }
    else {
        schtasks /delete /tn "VMware-Tools-Upgrade-Restart" /f
        schtasks /create /sc once /tn "VMware-Tools-Upgrade-Restart" /tr "shutdown -r" /st $restart_time /ru "SYSTEM"
    }

```

## SQL WHERE Query with to values
```sql
SELECT [ModuleAndEventText]
      ,[Time]
  FROM [mydatabase].[dbo].[event]
  WHERE [ModuleAndEventText] LIKE '%userus%' AND [ModuleAndEventText] LIKE '%new session%'
  ORDER BY [Time] DESC;
```

## Cant uninstall msi
[Microsoft-KB](https://support.microsoft.com/en-us/topic/fix-problems-that-block-programs-from-being-installed-or-removed-cca7d1b6-65a9-3d98-426b-e9f927e1eb4d)

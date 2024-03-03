---
tags:
    - microsoft
    - windows
    - exchange
    - exchange-server
    - distribution-group
    - member
---

# Mailboxes
## Mailbox Size for Users per Domain
The below command needs to be run in the **Exchange-Management Shell** and lists all Mailboxes sorted by TotalItemsize for a specific Domain.
```powershell
Get-Mailbox -ResultSize Unlimited | Where {$_.EmailAddresses -like "*@domain.de"} | Get-MailboxStatistics | sort-object TotalItemsize | FT DisplayName,TotalItemSize
```

## Export all Mailboxes with Domains to a File
The below command needs to be run in the **Exchange-Management Shell** and exports all Mailboxes for a specific Domain to a CSV file.
```powershell
Get-Mailbox "*@domain.de" -ResultSize Unlimited | ft -AutoSize DisplayName,PrimarySmtpAddress | export-csv "$env:Userprofile\Desktop\mailboxes.csv" -Delimiter ";" -NoType -Encoding UTF8
```

## Show all distribution groups with members
The below command needs to be run in the **Exchange-Management Shell** and shows all distribution groups with its members.
Display should not be truncated
```powershell
$FormatEnumerationLimit = -1
```

```powershell
Get-DistributionGroup -OrganizationalUnit "domain.local/MyOU/" | Select-Object -Property @{label='Gruppe';expression={$_.PrimarySmtpAddress}}, @{label='Mitglieder';expression={(Get-DistributionGroupMember $_.Name).PrimarySmtpAddress}} | fl
```

## Show folder count for mailbox
The below command needs to be run in the **Exchange-Management Shell** and shows all the folder count of the mailbox.
```powershell
Get-MailboxFolderStatistics -Identity mail@domain.de | Measure-Object | Select-Object -ExpandProperty Count
```

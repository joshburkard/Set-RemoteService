# Set-RemoteService

## description

This script allows it to set the status of a service on a remote computer

## examples

### without parameters

if you start this script without parameters, it will prompts to input this values:

- ComputerName (if leaved empty, the local computer will be used)
- ServiceName
- Different Credentials? (only if not local computer, acceppt Y or N)
- Credential

```PowerShell
.\Set-RemoteService.ps1
```

### start a service on the local computer

```PowerShell
.\Set-RemoteService.ps1 -ComputerName . -ServiceName 'BITS' -Action START
```

### start a service on a remote computer

```PowerShell
.\Set-RemoteService.ps1 -ComputerName 'server.domain.net' -ServiceName 'BITS' -Action START
```

### start a service on a remote computer with different credentials

```PowerShell
$Credential = Get-Credential
# or
$Credential = New-Object System.Management.Automation.PSCredential ( $Username, ( ConvertTo-SecureString $Password -AsPlainText -Force ) )

.\Set-RemoteService.ps1 -ComputerName 'server.domain.net' -ServiceName 'BITS' -Action START -Credential $Credential
```

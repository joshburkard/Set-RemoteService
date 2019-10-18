# Set-RemoteService

## description

This script allows it to set the status of a service on a remote computer

## parameters

### -ComputerName [string]

defines the name of the computer

this parameter is not mandatory. if it is empty, the script will prompt for the name

user **.** (a single point) for the local computer

```
Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```

### -ServiceName [string]

 defines the name of the service

this parameter is not mandatory. if it is empty, the script will prompt for the name

```
Required?                    false
Position?                    2
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```

### -Credential [System.Management.Automation.PSCredential]

defines the credential to access the remote computer

this parameter is not mandatory. if not defined the current users credentials will be used

```
Required?                    false
Position?                    3
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```

### -Action [string]

which action should be executed

allows this actions:

- START
- STOP
- RESTART

this parameter is not mandatory. if not defined, the default 'Start' will be used

```
Required?                    false
Position?                    4
Default value
Accept pipeline input?       false
Accept wildcard characters?  false
```

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

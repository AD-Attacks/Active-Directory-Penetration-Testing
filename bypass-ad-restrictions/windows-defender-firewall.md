# Windows Firewall

### List firewall state and current configuration

```
netsh firewall show state
netsh firewall show config
netsh advfirewall show allprofiles
```

### List the firewall's blocked ports

{% code overflow="wrap" %}
```
$f=New-object -comObject HNetCfg.FwPolicy2;$f.rules |  where {$_.action -eq "0"} | select name,applicationname,localports
```
{% endcode %}

### Disable firewall

We can disable the Firewall using multiple commands:

{% tabs %}
{% tab title="CMD" %}
{% code overflow="wrap" %}
```
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server"  /v fDenyTSConnections /t REG_DWORD /d 0 /f
```
{% endcode %}
{% endtab %}

{% tab title="Powershell" %}
{% code overflow="wrap" %}
```
powershell.exe -ExecutionPolicy Bypass -command 'Set-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name "fDenyTSConnections" –Value'`
```
{% endcode %}
{% endtab %}

{% tab title="NetSH" %}
```
netsh firewall set opmode disable
netsh Advfirewall set allprofiles state off
```
{% endtab %}
{% endtabs %}

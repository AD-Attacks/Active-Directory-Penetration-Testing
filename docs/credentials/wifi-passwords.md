# Wifi Passwords

```
Get-ChildItem -Recurse -Force -Include *wifi*
#List saved Wifi using
netsh wlan show profile
```

### To get the clear-text password use

```
netsh wlan show profile <SSID> key=clear
```

### Oneliner to extract all wifi passwords

{% code overflow="wrap" %}
```powershell
cls & echo. & for /f "tokens=4 delims=: " %a in ('netsh wlan show profiles ^| find "Profile "') do @echo off > nul & (netsh wlan show profiles name=%a key=clear | findstr "SSID Cipher Content" | find /v "Number" & echo.) & @echo on
```
{% endcode %}

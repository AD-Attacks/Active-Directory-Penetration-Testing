# 🤯 Pass the \*shit

### Over-Pass-the-Hash

Pass-the-Hash (PtH) involves an attacker using a valid NTLM hash instead of a plain text password to authenticate to a networked service. The approach bypasses the need for the actual plaintext password, making it a powerful technique for lateral movement within a network following the initial compromise.

{% code overflow="wrap" %}
```
Invoke-Mimikatz -Command '"sekurlsa::pth /domain:<computer> /user:Administrator /ntlm:<hash> /run:powe
```
{% endcode %}

<details>

<summary>T1550.002</summary>



</details>

### Pass the Ticket

Pass-the-Ticket (PtT) is an attack method where attackers steal Kerberos tickets from a compromised system and then use those tickets to authenticate as the ticket's original owner. Unlike Pass-the-Hash, Pass-the-Ticket specifically targets the Kerberos authentication protocol used within Windows Active Directory environments.

#### T1550.003

This technique identifier refers to the "Pass the Ticket" attack within MITRE ATT\&CK framework, emphasizing the method's relevance in understanding and mitigating cybersecurity threats.

### Pass the Cookie

### Pass the Ticket

<details>

<summary>T1550.003</summary>



</details>

Pass-the-Ticket – Requires access as user. Use to pivot

### Pass the Certificate

Pass-the-Certificate – Exploits systems by using stolen certificates to authenticate as other users. Similar to pass-the-ticket, this technique can be used for lateral movement and accessing sensitive resources without the need for the user's password.

---
description: Learn how to conduct an Internal Spearfishing attacks and test your end users.
---

# Internal Spearfishing

<details>

<summary>ID: <a href="https://attack.mitre.org/versions/v12/techniques/T1534/">T1534 </a>Tactic: Lateral Movement</summary>

Adversaries may use internal spearphishing to gain access to additional information or exploit other users within the same organization after they already have access to accounts or systems within the environment.

</details>

## MailSniper

MailSniper is a penetration testing tool for searching through email in a Microsoft Exchange environment for specific terms (passwords, insider intel, network architecture information, etc.). It can be used as a non-administrative user to search their own email or by an Exchange administrator to search the mailboxes of every user in a domain.

{% embed url="https://github.com/dafthack/MailSniper" %}

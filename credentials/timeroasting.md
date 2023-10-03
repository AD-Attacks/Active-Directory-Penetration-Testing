---
description: >-
  Timeroasting takes advantage of Windows' NTP authentication mechanism,
  allowing unauthenticated attackers to effectively request a password hash of
  any computer or trust account by sending an NTP ...
coverY: 0
---

# 🟢 Timeroasting

Timeroasting takes advantage of Windows' NTP authentication mechanism, allowing unauthenticated attackers to effectively request a password hash of any computer or trust account by sending an NTP request with that account's RID.&#x20;

This is not a problem when computer accounts are properly generated, but if a non-standard or legacy default password is set this tool allows you to brute-force those offline.

{% embed url="https://github.com/SecuraBV/Timeroast/tree/main" %}

{% embed url="https://www.secura.com/uploads/whitepapers/Secura-WP-Timeroasting-v3.pdf" %}

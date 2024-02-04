---
description: >-
  Dive into our comprehensive article on Kerberoasting, a threat technique
  utilized in cybersecurity. Understand its significance, potential impact and
  preventive methods.
---

# 🟢 Kerberoasting

#### Understanding Kerberoasting

Kerberoasting is a type of cyber attack that targets the Kerberos authentication protocol widely utilized in Windows networks. It specifically aims to extract service account credentials by taking advantage of the way Kerberos handles service tickets.

When a user or service requests access to a resource from the Key Distribution Center (KDC), the KDC issues a Ticket Granting Ticket (TGT) and subsequently a Service Ticket (ST) if access to a service is required. These tickets are encrypted with the service's password hash.

**How Kerberoasting Works**

1. The attacker initially gains limited access to the network.
2. They request service tickets for various services on the network.
3. The service tickets, encrypted with the target service's password, are saved to the attacker's machine.
4. The attacker then attempts to offline-brute-force the encryption to reveal the service password.

**Implications of Kerberoasting**

* **Credential Theft**: Successful Kerberoasting attacks compromise service account credentials that can have extensive privileges.
* **Lateral Movement**: Attackers can use the stolen credentials to move laterally within the network, accessing sensitive data and systems.
* **Persistent Access**: With service account credentials, attackers potentially maintain long-term access to the network.

**Mitigation Strategies**

* Use strong, complex passwords for service accounts that are resistant to brute-force attacks.
* Regularly rotate service account passwords to limit the window of opportunity for attackers.
* Enable security features like Advanced Threat Analytics (ATA) for detecting anomalous activities related to Kerberos authentication.

Network administrators must monitor for unusual service ticket requests and investigate any signs of Kerberoasting to protect network resources and sensitive information.

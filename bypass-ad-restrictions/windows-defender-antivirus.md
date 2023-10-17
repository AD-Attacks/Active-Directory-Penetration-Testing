---
description: Byapss Windows Defender Antivirus
---

# 🟢 Windows Defender Antivirus

### Check status of Defender

```
PS C:\> Get-MpComputerStatus
```

### Disable scanning all downloaded files and attachments, disable AMSI (reactive)

```
PS C:\> Set-MpPreference -DisableRealtimeMonitoring $true; Get-MpComputerStatus
PS C:\> Set-MpPreference -DisableIOAVProtection $true
```

### Disable AMSI (set to 0 to enable)

```
PS C:\> Set-MpPreference -DisableScriptScanning 1
```

### Exclude a folder

```
PS C:\> Add-MpPreference -ExclusionPath "C:\Temp"
PS C:\> Add-MpPreference -ExclusionPath "C:\Windows\Tasks"
PS C:\> Set-MpPreference -ExclusionProcess "word.exe", "vmwp.exe"
```

### Remove signatures

{% hint style="info" %}
if the Internet connection is present, they will be downloaded again
{% endhint %}

{% code overflow="wrap" %}
```
PS > & "C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.9-0\MpCmdRun.exe" -RemoveDefinitions -All
PS > & "C:\Program Files\Windows Defender\MpCmdRun.exe" -RemoveDefinitions -All
```
{% endcode %}

### Disable real-time protection (proactive):

```
PS > Set-MpPreference -DisableRealTimeMonitoring $true
```

Disable scanning all downloaded files and attachments, and disable AMSI (reactive):

```
PS > Set-MpPreference -DisableIOAVProtection $true
```

Remove signatures (if Internet connection is present, they will be downloaded again):

```
PS > cd "C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2008.9-0"
PS > .\MpCmdRun.exe -RemoveDefinitions -All
Or
Cmd > "%PROGRAMFILES%\Windows Defender\MpCmdRun.exe" -RemoveDefinitions -All
```

## Lower Token Integrity

* [https://elastic.github.io/security-research/whitepapers/2022/02/02.sandboxing-antimalware-products-for-fun-and-profit/article/](https://elastic.github.io/security-research/whitepapers/2022/02/02.sandboxing-antimalware-products-for-fun-and-profit/article/)
* [https://github.com/plackyhacker/SandboxDefender](https://github.com/plackyhacker/SandboxDefender)
* [https://github.com/pwn1sher/KillDefender](https://github.com/pwn1sher/KillDefender)
* [https://github.com/googleprojectzero/sandbox-attacksurface-analysis-tools](https://github.com/googleprojectzero/sandbox-attacksurface-analysis-tools)

## Disable Defender

* [https://github.com/mandiant/commando-vm#pre-install-procedures](https://github.com/mandiant/commando-vm#pre-install-procedures)
* [https://github.com/swagkarna/Defeat-Defender-V1.2](https://github.com/swagkarna/Defeat-Defender-V1.2)
* [https://github.com/APTortellini/DefenderSwitch](https://github.com/APTortellini/DefenderSwitch)
* [https://github.com/dosxuz/DefenderStop](https://github.com/dosxuz/DefenderStop)
* [https://gist.github.com/fiercebrute/46e0636c0eaf72dcd3df4e280b6792d6](https://gist.github.com/fiercebrute/46e0636c0eaf72dcd3df4e280b6792d6)
* [http://www.wxxy-sec.com/?p=154](http://www.wxxy-sec.com/?p=154)
* gpedit.msc > _Administrative Templates_ > _Windows Components_ > _Microsoft Defender Antivirus_ > _Real-time Protection_ > _Turn off real-time protection_ > _Enabled_ ✔
* gpedit.msc > _Administrative Templates_ > _Windows Components_ > _Microsoft Defender Antivirus_ > _Turn off Microsoft Defender Antivirus_ > _Enabled_ ✔

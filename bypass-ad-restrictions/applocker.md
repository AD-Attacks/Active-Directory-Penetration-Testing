# AppLocker

Organizations also often focus on blocking the `PowerShell.exe` executable, but forget about the other [PowerShell executable locations](https://www.powershelladmin.com/wiki/PowerShell\_Executables\_File\_System\_Locations) such as `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe` or `PowerShell_ISE.exe`. We can see that this is the case in the `AppLocker` rules shown below. All Domain Users are disallowed from running the 64-bit PowerShell executable located at:

`%SystemRoot%\system32\WindowsPowerShell\v1.0\powershell.exe`

So, we can merely call it from other locations. Sometimes, we run into more stringent `AppLocker` policies that require more creativity to bypass.&#x20;

```
PS C:\htb> Get-AppLockerPolicy -Effective | select -ExpandProperty RuleCollections
```

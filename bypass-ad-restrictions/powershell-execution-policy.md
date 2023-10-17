---
description: >-
  Bypass PowerShell Execution Policy is a rule that determines what kind of
  PowerShell scripts and commands you are allowed to run on your computer.
---

# 🟢 PowerShell Execution Policy

The PowerShell Execution Policy is a rule that determines what kind of PowerShell scripts and commands you are allowed to run on your computer. It is like a safety gate that checks if the scripts or commands you want to use are safe or not.

**There are different levels of the PowerShell Execution Policy:**

1. **Restricted:** This is the strictest policy. It's like saying you can't play with any PowerShell toys at all. You're not allowed to run any scripts or commands. It's for your own protection, but it also means you can't do anything cool with PowerShell.
2. **AllSigned:** This policy is a bit more relaxed. It means you can only play with PowerShell toys that are signed by a trusted grown-up. It's like your parents checking that a toy is safe before letting you play with it. This way, you can use scripts and commands that have been checked and approved.
3. **RemoteSigned:** With this policy, you can play with PowerShell toys that you or someone you trust created on your own computer. However, if the toys come from somewhere else, like the internet, they need to be signed by a trusted grown-up just like in the AllSigned policy.
4. **Unrestricted:** This policy is like having no rules at all! It means you can play with any PowerShell toy you want, whether it's signed or not. However, just like with real toys, you need to be careful because you might accidentally hurt yourself if you don't know what you're doing.\


```powershell
powershell -ExecutionPolicy bypass
```

```powershell
powershell -c whoami
```

```
powershell -ep bypass ./PowerView.ps1
```

```powershell
powershell -encodedcommand $env:PSExecutionPolicyPreference =="bypass"
```

### Change Execution Policy

```powershell
Set-Executionpolicy -Scope CurrentUser -ExecutionPolicy UnRestricted
```

```powershell
Set-ExecutionPolicy Bypass -Scope Process
```

* [https://blog.netspi.com/15-ways-to-bypass-the-powershell-execution-policy/](https://blog.netspi.com/15-ways-to-bypass-the-powershell-execution-policy/)
* [https://bestestredteam.com/2019/01/27/powershell-execution-policy-bypass/](https://bestestredteam.com/2019/01/27/powershell-execution-policy-bypass/)

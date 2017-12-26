# Windows Home
### Active RDP In Windows 10 home
~> Download: RDPWrap

From link ~> https://github.com/stascorp/rdpwrap/releases

Test on: RDPWrap-v1.6.1

-----------------------

### Install gpedit.msc on Windows 10 home
``` bat
@echo off 
pushd "%~dp0" 

dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt 
dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt 

for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i" 
pause
```

# Windows Enterprise
### Windows 10 wifi error "No internet, secured" solved 

https://answers.microsoft.com/en-us/ie/forum/ie11-iewindows_10/windows-10-wifi-error-no-internet-secured-solved/07e3e865-0cba-4f05-9b73-2b480cd1c322?auth=1

```plaintest
1. Go to Control Panel >Network and Internet> Network Connections

2. Choose your wifi connection, right-click and select Properties

3. In the Wi-Fi Properties, in the "This connection uses the following items:" tab, you should check the following options:

   > Client for Microsoft Networks
   > File and Printer Sharing for Microsoft Networks
   > Link-Layer Topology Discovery Mapper I/O Driver
   > Internet Protocol Version 4 (TCP/IPv4)
   > Reliable Multicast Protocol
   > Internet Protocol Version 6 (TCP/IPv6)
   > Link-Layer Topology Discovery Responder
```

### fix black screen windows 10
https://www.windowscentral.com/how-fix-black-screen-problems-windows-10

remove VGA driver from safe mode
for goes to safe mode frist restart your system and press shift

   > 1. trubleshoot
   
   > 2. advance mode
   
   > 3. sturtup settings
   
   > 4. restat
   
   > 5. F5
   
   > 6. unistall "Display Adapters" without checkbox
   
   > 7. restart your system

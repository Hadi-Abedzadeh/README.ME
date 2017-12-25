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
## Windows 10 wifi error "No internet, secured" solved 

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

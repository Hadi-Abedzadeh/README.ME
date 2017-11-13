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

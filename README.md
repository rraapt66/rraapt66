net stop appidsvc
net stop bits
net stop cryptsvc
net stop msiserver
net stop wuauserv
PowerShell -ExecutionPolicy Unrestricted -Command "& {$manifest = (Get-AppxPackage Microsoft.WindowsStore).InstallLocation + '\AppxManifest.xml' ; Add-AppxPackage -DisableDevelopmentMode -Register $manifest}"
net stop appidsvc
net stop bits
net stop cryptsvc
net stop msiserver
net stop wuauserv
Del "%ALLUSERSPROFILE%\Application Data\Microsoft\Network\Downloader\qmgr*.dat" /f /q
Del "C:\Windows\Logs\CBS\*.*" /f /s /q
Del "C:\Windows\Logs\DISM\*.*" /f /s /q
Del "C:\Windows\Logs\WindowsUpdate\*.*" /f /s /q
Del "C:\Windows\Temp\*.*" /f /s /q
Ren %systemroot%\SoftwareDistribution SoftwareDistribution.bak
Ren %systemroot%\system32\catroot2 catroot2.bak
bitsadmin.exe /reset /allusers
netsh winsock reset
shutdown -r -f -t 1

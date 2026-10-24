# Investigation additional notes

#1. Initial investigation begins
* I had set up my Ubuntu UTM Windows machine and began understanding the terrain using various commands
* The first command I utilized to help me discover the commands I needed was Get-Command **, (example: Get-Command *process*) to obtain process related commands 


#2.Local accounts enumerated
* 21 groups were found
* command used: (Get-LocalGroup).count


#3.Processes and services baseline
* Found a total number of 145 processes running
* Total number of services running were 268, 179 of them were stopped
* Two processes I investigated were WindowsTerminal.exe and PowerShell.exe
* I learned WindowsTerminal.exe acts as a UI layer that runs and manages other command-line shells
* PowerShell simply launches the executable file for PowerShell
* Commands used: Get-Command *process*, Get-Process, (Get-Process).Count, (Get-Service).Count, Get-Service | Object-status


#4. Network configurations and TCP connections examined
* 3 established internet connections going to port 443 (HTTPS)
* Commands used: Get-NetConnectionProfile, Get-NetIPConfiguration, Get-NetTCPConnection -State Established | Select-Object -First 10 LocalPort, RemoteAddress, OwningProcess


#5 Selected Windows event logs examined further
* Number of total application entries: 356
* Security entries: 20,745
* System entries: 1,168
* Windows PowerShell entries: 80
* Commands used: Get-EventLog, GetEventLog-List, Get-WinEvent -LogName Security -MaxEvents 20 | Select-Object TimeCreated, ID, ProviderName, Message


Startup/Persistence locations: 
* Startup names: OneDriveSetup, OneDrive, MicrosoftEdgeAutolLaunch, SecurityHealth
* Persistence Locations:  All legit; no suspicious persistence locations found.
* Commands used to investigate startup and persistence locations:  Get-CimInstance Win32_StartupCommand | Select-Object Name, Command, Location, User; Get-ItemProperty HKLM:\Software\Microsoft\Windows\CurrentVersion\Run; Get-ScheduledTask | Where-Object {$_.TaskPath -notlike "\Microsoft*"}

------

Suspicious Files: 
In order to search for any suspicious files, i used a specially crafted command to output any anomolies; upon reading the output i noticed ‘blnsvr.exe’,  i then checked if its signature was valid to which the status was ‘Unkownerror’, in order to finally verify what this file could have been i used a final command to verify its full path and the output seemed to connect to the fact that i am using a VM and this is a common service intended for that.

File investigated: ‘blnsvr’
* Full path: c”\program files (x86)\UTM guest tools\drivers\balloon\w11\amr64\balnsvr.exe’
* Signature status\message: UnknownError, ‘A certificate chain processed, but terminated in a root certificate, which is not trusted by the trust provider.’
* Issuer: CN=Red Hat Inc, OU=Dev, O=virtio-win
* What was found: I found this file is likely related to the Windows VM that I am running this on, and its lack of validity is due to the issuer being Red Hat, which is not included in Microsoft’s standard trusted root certification authorities store, resulting in the UnknownError message.


PowerShell commands used to verify this file:   Get-Process | Where-Object {$_.MainModule.FileName} | ForEach-Object {
    Get-AuthenticodeSignature $_.MainModule.FileName -ErrorAction SilentlyContinue
} | Where-Object {$_.Status -ne "Valid"} | Select-Object Status, Path | Unique, Get-Authenitcodesignature, Get-Process blnsvr | Select-Object -property Path

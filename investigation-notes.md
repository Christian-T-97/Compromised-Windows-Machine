# Investigation additional notes

##1. Initial investigation begins
* I had set up my Ubuntu UTM Windows machine and began understanding the terrain using various commands
* The first command I utilized to help me discover the commands I needed was Get-Command **, (example: Get-Command *process*) to obtain process related commands 


##2.Local accounts enumerated
* 21 groups were found
* command used: (Get-LocalGroup).count


##3.Processes and services baseline
* Found a total number of 145 processes running
* Total number of services running were 268, 179 of them were stopped
* Two processes I investigated were WindowsTerminal.exe and PowerShell.exe
* I learned WindowsTerminal.exe acts as a UI layer that runs and manages other command-line shells
* PowerShell simply launches the executable file for PowerShell
* Commands used: Get-Command *process*, Get-Process, (Get-Process).Count, (Get-Service).Count, Get-Service | Object-status


##4. Network configurations and TCP connections examined
* 3 established internet connections going to port 443 (HTTPS)
* Commands used: Get-NetConnectionProfile, Get-NetIPConfiguration, Get-NetTCPConnection -State Established | Select-Object -First 10 LocalPort, RemoteAddress, OwningProcess


##5 Selected Windows event logs examined further
* Number of total application entries: 356
* Security entries: 20,745
* System entries: 1,168
* Windows PowerShell entries: 80
* Commands used: Get-EventLog, GetEventLog-List, Get-WinEvent -LogName Security -MaxEvents 20 | Select-Object TimeCreated, ID, ProviderName, Message



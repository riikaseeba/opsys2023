# Skriptimine Windowsis

Skriptimise kasu avaldub tihti alles siis, kui peate suurt kogust (üle 10) arvuteid üksinda haldama. 
Käesolevas praktikumis näidati mulle, kuidas antud ülesande lahendamist oluliselt kiirendada. 
Selle praktikumi eesmärk oli anda ülevaatlik sissejuhatus Powershelli eripäradesse ja kasutamisse Windowsis.

Praktikum kujunes sujuvalt. Aega tööle keskendumisele ja skripti koostamisele kulus ligikaudu viis tundi. Ülesannete lahenduse leiab siit aruandest "_Iseseisva töö Lahendus_" alt.

## Konspekt endale
Kokkuvõtvalt võiks öelda, et PowerShell on automatiseerimismootor, mis võimaldab kaugligipääsu
erinevatele arvutitele, asünkroonset protsessimist ning tänu WMI (Windows Management
Instrumentation), COM- ja .NET komponentidele lihtsale kasutusvõimalusele on see väga hõlpsasti
laiendatav.

PowerShelli teeb võrreldes teiste käsuridadega eriliseks asjaolu, et tegemist on objekt orienteeritud
käsureaga. See tähendab, et erinevate käskude sisendid ja väljundid ei ole mitte lihtsad tekstistringid
vaid objektid. 

*  <img width="294" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/018a7a6b-0b7b-4c45-875e-51778e70872f">

# Iseseisva töö Lahendus
* Väljund failis:

      Masina nimi: Seeba-W11
      PowerShelli versioon: 5.1.22621.2506
      Windowsi versioon: 10.0.22631.0
      
      IPAddress                              IPSubnet            DefaultIPGateway DHCPEnabled MAC
                                                                                              Add
                                                                                              res
                                                                                              s  
      ---------                              --------            ---------------- ----------- ---
      {10.0.2.15, fe80::5b48:dfc9:8dee:51a9} {255.255.255.0, 64} {10.0.2.2}              True 08:
      {172.18.131.31}                        {255.255.255.255}   {0.0.0.0}              False 02:
      
      
      
      
      Model      Manufacturer TotalPhysicalMemory
      -----      ------------ -------------------
      VirtualBox innotek GmbH          4814737408
      
      
      
      
      Name                               DriverVersion DriverDate                VideoModeDescrip
                                                                                 tion            
      ----                               ------------- ----------                ----------------
      VirtualBox Graphics Adapter (WDDM) 7.0.10.8379   20230712000000.000000-000 958 x 1079 x ...
      
      
      
      
      Model                Size
      -----                ----
      VBOX HARDDISK 68713989120
      
      
      
      Vaba ruumi C:-kettal: 27.3712120056152 GB
      
      
      Name               Description                                                             
      ----               -----------                                                             
      Administrator      Built-in account for administering the computer/domain                  
      DefaultAccount     A user account managed by the system.                                   
      Guest              Built-in account for guest access to the computer/domain                
      riika                                                                                      
      Riika-tava                                                                                 
      tootaja1                                                                                   
      tootaja2                                                                                   
      WDAGUtilityAccount A user account managed and used by the system for Windows Defender Ap...
      ylemus                                                                                     
      
      
      
      Käimasolevate protsesside arv: 130
      
      Name                   ProcessId StartTime          
      ----                   --------- ---------          
      svchost.exe                 3576 18.12.2023 20:52:39
      SearchFilterHost.exe        7720 18.12.2023 20:52:33
      smartscreen.exe              332 18.12.2023 20:52:28
      SearchProtocolHost.exe      7684 18.12.2023 20:51:44
      WmiPrvSE.exe                7984 18.12.2023 20:43:52
      WmiPrvSE.exe                2556 18.12.2023 20:11:04
      conhost.exe                 6856 18.12.2023 19:57:14
      powershell_ise.exe          7648 18.12.2023 19:51:36
      svchost.exe                 4372 18.12.2023 19:48:27
      dllhost.exe                 7120 18.12.2023 19:38:07
      
      
      
      Arvuti kuupäev ja kellaaeg: 12/18/2023 20:52:48


* Skript:

      $OutputFile = "C:\Users\riika\Documents\praktikum13\systeemiinfo.txt"
      
      # Masina nimi, PowerShelli versioon ja Windowsi versioon
      $Hostname = hostname
      $PSVersion = $PSVersionTable.PSVersion
      $OSVersion = [System.Environment]::OSVersion.Version
      "Masina nimi: $Hostname" | Out-File $OutputFile
      "PowerShelli versioon: $PSVersion" | Out-File $OutputFile -Append
      "Windowsi versioon: $OSVersion" | Out-File $OutputFile -Append
      
      # Võrgu konfiguratsioon
      $IPConfig = Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Where-Object { $_.IPAddress -ne $null } | Format-Table IPAddress, IPSubnet, DefaultIPGateway, DHCPEnabled, MACAddress -AutoSize | Out-String
      $IPConfig | Out-File $OutputFile -Append
      
      # Arvuti protsessori kirjeldus ja põhimälu RAM kogus
      $SystemInfo = Get-WmiObject -Class Win32_ComputerSystem | Format-Table Model, Manufacturer, TotalPhysicalMemory -AutoSize | Out-String
      $SystemInfo | Out-File $OutputFile -Append
      
      # Graafikakaardi nimi, draiveri versioon, kuupäev ja ekraani lahutus
      $GraphicsCard = Get-WmiObject -Class Win32_VideoController | Format-Table Name, DriverVersion, DriverDate, VideoModeDescription -AutoSize | Out-String
      $GraphicsCard | Out-File $OutputFile -Append
      
      # Arvuti kõvaketaste informatsioon
      $DiskInfo = Get-WmiObject -Class Win32_DiskDrive | Format-Table Model, Size -AutoSize | Out-String
      $FreeSpace = Get-WmiObject -Class Win32_LogicalDisk | Where-Object { $_.DeviceID -eq "C:" } | Select-Object FreeSpace
      $DiskInfo | Out-File $OutputFile -Append
      "Vaba ruumi C:-kettal: $($FreeSpace.FreeSpace / 1GB) GB" | Out-File $OutputFile -Append
      
      # PCI-siinil olevate seadmete draiverite info
      $PCIDevices = Get-WmiObject Win32_PnPSignedDriver| where {$_.DeviceClass -eq "PCI"} | Format-Table DeviceName, Manufacturer, DriverVersion -AutoSize | Out-String
      $PCIDevices | Out-File $OutputFile -Append
      
      # Arvutis olevad kasutajad
      $Users = Get-WmiObject -Class Win32_UserAccount | Format-Table Name, Description, LocalAccount, Disabled -AutoSize | Out-String
      $Users | Out-File $OutputFile -Append
      
      # Käimasolevate protsesside arv
      $ProcessCount = (Get-Process).Count
      "Käimasolevate protsesside arv: $ProcessCount" | Out-File $OutputFile -Append
      
      # 10 viimasena käivitatud protsessi
      $LastProcesses = Get-WmiObject Win32_Process | Select-Object Name, ProcessId, @{Name='StartTime';Expression={$_.ConvertToDateTime($_.CreationDate)}} | Sort-Object StartTime -Descending | Select-Object -First 10 | Format-Table -AutoSize | Out-String
      $LastProcesses | Out-File $OutputFile -Append
      
      # Arvuti kuupäev ja kellaaeg
      $DateTime = Get-Date
      "Arvuti kuupäev ja kellaaeg: $DateTime" | Out-File $OutputFile -Append

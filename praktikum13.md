# Skriptimine Windowsis
ajakulu:
*  10:51 -

 Skriptimise kasu avaldub tihti alles siis, kui peate suurt kogust (üle 10) arvuteid üksinda haldama. Käesolevas praktikumis näidati mulle, kuidas antud ülesande lahendamist oluliselt kiirendada. 
 Selle praktikumi eesmärk oli anda ülevaatlik sissejuhatus Powershelli eripäradesse ja kasutamisse Windowsis.

## Konspekt
Kokkuvõtvalt võiks öelda, et PowerShell on automatiseerimismootor, mis võimaldab kaugligipääsu
erinevatele arvutitele, asünkroonset protsessimist ning tänu WMI (Windows Management
Instrumentation), COM- ja .NET komponentidele lihtsale kasutusvõimalusele on see väga hõlpsasti
laiendatav.

PowerShelli teeb võrreldes teiste käsuridadega eriliseks asjaolu, et tegemist on objekt orienteeritud
käsureaga. See tähendab, et erinevate käskude sisendid ja väljundid ei ole mitte lihtsad tekstistringid
vaid objektid. 

*  Kõiki PowerShellis kasutatavaid tegusõnu saate pärida käsuga
    *     Get-Verb
*  Kasutatavate käskude nimekirja saate pärida käsuga
    *     Get-Command
*  Kui paljude skriptikeelte juures on sellised funktsioonid vaja ise koostada, siis PowerShellil on need koheselt olemas. Selliste käskude nimekirja saate pärida sisestades käsureale
    *     Get-Command *-object
    * Käsklusele lisatud parameeter _\*- object_ tähendab, et filtreeri käskluse kõikidest tulemustest välja ainult need, mis lõppevad „-object“ (\* tähendab, et algus võib olla suvaline).
*  <img width="294" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/018a7a6b-0b7b-4c45-875e-51778e70872f">


### Ülesanne 1
Väljund failis:

    Masina nimi: Seeba-W11 
    PowerShelli versioon: 5.1.22621.2506 
    Windowsi versioon: 10.0.22631.0

Skript:

    # Masina nimi
    $hostname = hostname
    
    # PowerShelli versioon
    $powershell_version = $PSVersionTable.PSVersion
    
    # Windowsi versioon
    $windows_version = [System.Environment]::OSVersion.Version
    
    # Info salvestamine faili
    $info = "Masina nimi: $hostname `nPowerShelli versioon: $powershell_version `nWindowsi versioon: $windows_version"
    $info | Out-File -FilePath .\yl1

### Ülesanne 2
Väljund failis:

    IP-aadress: 10.0.2.15
    Võrgumask: 255.255.255.0
    Gateway: 10.0.2.2
    DHCP lubatud: True False
    MAC-aadress: 08:00:27:CC:C8:FB 02:50:41:00:00:01

Skript:

    # Skripti algus
    $networkInfo = Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE
    
    # Võrguinfo kogumine
    $ipAddress = $networkInfo.IPAddress[0]
    $subnetMask = $networkInfo.IPSubnet[0]
    $defaultGateway = $networkInfo.DefaultIPGateway[0]
    $dhcpEnabled = $networkInfo.DHCPEnabled
    $macAddress = $networkInfo.MACAddress
    
    # Info väljastamine
    $info = @"
    IP-aadress: $ipAddress
    Võrgumask: $subnetMask
    Gateway: $defaultGateway
    DHCP lubatud: $dhcpEnabled
    MAC-aadress: $macAddress
    "@
    
    # Info kirjutamine faili
    $info | Out-File -FilePath .\v6rgu_info.txt

### Ülesanne 3
Väljund failis:

    Protsessori kirjeldus: x64-based PC
    Põhimälu RAM kogus (GB): 4.48

Skript:

    $computerSystem = Get-WmiObject -Class Win32_ComputerSystem
    
    # Arvutiinfo kogumine
    $processorDescription = $computerSystem.SystemType
    $totalPhysicalMemory = [math]::Round(($computerSystem.TotalPhysicalMemory / 1GB), 2)
    
    # Info väljastamine
    $info = @"
    Protsessori kirjeldus: $processorDescription
    Põhimälu RAM kogus (GB): $totalPhysicalMemory
    "@
    
    # Info kirjutamine faili
    $info | Out-File -FilePath .\arvuti.txt

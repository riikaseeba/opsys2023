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
    #$nr:	küsimuse number
    #$param: mis parameetriga tegemist (võimalikult lühidalt)
    #$sisu:	väljastatav sisu
    function valjasta{
    	param ($nr, $param, $sisu)
    	$fail = ".\tulemus.txt"
    	$aeg = Get-Date -Format "HH:mm:ss.fff"
    	if($sisu -eq $null){
    		$rida = "$nr.	$aeg	${param}:	NULL"
    		Write-Output $rida
    		$rida | Out-File -FilePath $fail -Append
    	}elseif($sisu.GetType().Name -eq "Object[]"){
    		$rida = "$nr.	$aeg	${param}:"
    		Write-Output $rida $sisu
    		$rida | Out-File -FilePath $fail -Append
    		$sisu | Out-File -FilePath $fail -Append
    	}else{
    		$rida = "$nr.	$aeg	${param}:	$sisu"
    		Write-Output $rida
    		$rida | Out-File -FilePath $fail -Append
    	}
    }
    
    [int]$aegA = (Get-Date).Millisecond
    Valjasta 0 "ALGUS" ("Aeg: "+(Get-Date -Format "dddd MM/dd/yyyy HH:mm K")+" Teostaja: Riika")
    Valjasta 1 "host" (hostname)
    
    #Tee oma tegevused ja väljasta tulemused funktsiooni abil (võib funktsiooni ise täiendada soovi korral)
    #...
    
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

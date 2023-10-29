# Haakimine

## 1. Windows 11 Kettahaldus
### Miks andmekandjad vajavad lähtestamist? 

Lähtestamine taastab seadme algse konfiguratsiooni. See tähendab, et enne lähtestamist peab tagama eelnevate andmete varundamise, et andmed ise saaksid säilida ning vajadusel taastada.
Lähtestamine on vajalik, et saaks andmed kustutada andmekandjast enne müüki panekut, kuid see pole ainus põhjus.
Seda kasutatakse ka tõrkeotsingute puhul, tulemüüri probleemide lahendamiseks, andmete taastamiseks või andmete kustutamiseks.
 
### Millised on GPT kasutamise eelised võrreldes MBRiga? (Tooge välja vähemalt 3 eelist).

GPT-l on suurem partitsioonide arv ja suurus, s.t GPT toetab väga suuri partitsioone, samal ajal MBR aga piirab partitsioonide suurust umbes 2 TB-ga.
GPT annab suurema andmete kaitse ja ühilduvuse UEFI-põhiste süsteemidega. MBR on võib-olla sobivam vanematele arvutitele.
GPT sisaldab varukoopiaid partitsioonitabelist, mis muudab selle vastupidavamaks andmekandja rikke korral. MBR-il ei ole sisseehitatud varukoopiaid, mistõttu võib see põhjustada suuremat riski andmete kaotamisele.

## 2. Windows 11 võrgukettad
https://kodu.ut.ee/~riika/hdd.png

## 3. Serveris asuvate ketaste haakimine Ubuntus
käsu ls -la /mnt/ut/public_html väljundi pilt:

<img width="278" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/86423657-9dcc-4102-bbb1-a034c7ae7ea0">

## 4. Ubuntu graafiline kettahaldustöörist "Disks"
## 5. USB-mälupulga kasutamine Ubuntus
### Mida mõjutasid mount-käsu parameetrid -o ro ja -t auto?
**-o ro** - "read-only mode", s.t., et andmete kirjutamine kettale on keelatud.

**-t auto** - aitab automaatselt tuvastada andmekandja failisüsteemi tüübi.

### Leidke mount-käsu väljundist üles, mis väärtusega asendas Ubuntu auto-parameetri.
**/dev/sdc2 on /media/riika/riika type ntfs3 ** - /dev/sdc2 on haagitud /media/riika/riika kohale ning sellel on ntfs3 tüüpi failisüsteem.

## 6. 4TB ketta automaatne ühendamine arvuti käivitumisel
<img width="523" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/fc35baa8-6f36-4289-b0a2-71d84cdaa1be">


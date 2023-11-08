# Ressursihaldus
Käesolevas praktikumis tutvusin operatsioonisüsteemi ressurssidega. Selle sooritamiseks õpisin esmalt tundma erinevaid tööriistu nii Linuxis ja Windowsis.

## Vahekokkuvõte enda jaoks
### Tööriistad Windowsis 
*  **Tegumihaldur** -  Task Manageri abil on võimalik saada infot jooksvate protsesside ja ressursikasutuse hetkeolukorra kohta. Kiirklahvikombinatsioon avamiseks on **CTRL+SHIFT+ESC**
*  **Resource Monitor** - See kuvab detailsemat infot protsesside, teenuste, protsesside poolt kasutatavate lisamoodulite ja ressursside kohta.
*  **Performance Monitor** - Tööriist, mis võimaldab spetsiifilisi pikemaajalisi arvuti jõudlust mõõtvaid teste läbi viia.
*  **Kettahaldus** - salvestusseadmete haldamiseks mõeldud tööriist, mille abil saab vaadata ja muuta partitsioone, hallata RAID-massiive ja vormindada partitsioone erinevate failisüsteemide jaoks.
*  **Seadmehaldus** - haldusvahend, millega saab hallata arvutisiseste ja perifeerseadmete tööd. selle abil saab kontrollida näiteks katkestuste numbreid ja I/O aadressivahemikke. Katkestuste numbrite ja mäluaadressite vahemike vaatamiseks tuleb muuta Device Manageri peavaadet: View -> Resources by type
*  **Dxdiag** - Windowsi tööriist, mis kogub arvuti põhiinfo (protsessor, mälu, graafikaseadmed, olulisemad perifeerseadmed jne) ühte kohta ja kergesti käideldavasse formaati.
*  **Sysinternals Suite** -Sisaldab erinevaid programme Windowsis toimuva kohta info kuvamiseks.
*  **Process Explorer** - alternatiiv/täiendus Task Managerile, mille kasutajaliides ja võimalused on oluliselt keerulisemad. lisage veerge (column-e) algvaatesse olulise informatsiooni nägemiseks (parem hiireklahv üleval tulba nimede alal).
*  **Autoruns** - täiendus System Configurationile (käsurealt msconfig), mille abil on võimalik saada täpsemat infot kõikide automaatselt käivituvate protsesside ja teenuste kohta. Hea programm kurivara leidmiseks
*  **WinDirStat** - eraldi paigaldatav programm, mis võimaldab visuaalselt uurida Windows-arvuti ketta kasutust. Kui palju mingi fail või kaust salvestusmahtu enda alla võtab?

### Tööriistad Linuxis

## Ülesanded:
tabeli koostamise abiallikas: https://www.tablesgenerator.com/markdown_tables

| Küsimused 1-11 | Linux  | Windows  | Linuxis kasutatud käsklus	  | Windowsis kasutatud tööriist  |
|---|---|---|---|---|
| Mitu protsessi kokku arvutis käib?  |   | 145  |   | Tegumihaldur -> jõudlus -> protsessid |
| Milline on kõige esimesena käivitatud protsess?  |   | smss.exe |   |  Process Explorer -> Start Time |
| Milliste kasutajate protsesse arvutis käib?   |   | Tavakasutajad (Riika)  |   | Tegumihaldur -> kasutajad  |
| Kui kaua on arvuti järjest töötanud? |   |  0:01:00:29 |   |Tegumihaldud -> jõudlus -> tööaeg |
|  Milline protsess käivitati kõige hiljem? |   | svchost.exe  |   | Process Explorer -> Start Time  |
| Milline on kõige rohkem protsessoriaega võttev protsess?  |   | System Idle Process  |   | Process Explorer -> CPU  |
| Milline on kõige rohkem virtuaalmälu  võttev protsess? |   | Windows Feature Experience Pack  |   | Tegumihaldur -> rakenduse ajalugu  |
| Milline on kõige rohkem füüsilist mälu võttev protsess?  |   | Antimalware Service Executable  |   | Tegumihaldur -> mälu  |
|  Kui palju füüsilisest mälust on vaba? |   | 1,8GB  |   | Tegumihaldur -> jõudlus -> mälu -> saadaval  |
|  Kui palju on põhikettal (C:, /) vaba ruumi mahult (GB) ja protsentuaalselt? |   | 26,8GB ehk  42% |   | File Explorer -> See arvuti -> vaba maht (või parem hiirklahv -> atribuudid -> maht) |
| Milline on kõige suurem kõvakettal olev fail ja kõige suurem alamkaust?  |   |   |   |   |

## küsimused 12-15
### 12. (ainult Linuxis)

### 13. (Ainult Windowsis)

### 14. (Ainult Windowsis)

### 15. (vali  Linuxis või Windowsis)
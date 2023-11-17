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
*  **ps** - näitab hetkel käimasolevaid protsesse. **ps -ef** – näitab kõigi kasutajate protsesside tabelit.
*  pstree
*  **top** - kui palju protsessoriaega ja mälu hetkel kasutatakse
    * top -p pid väljastab info ühe protsessi kohta
    * top -b -d 5 -n 10 väljastab tulemuse iga 5 (lipp d) sekundi järel kokku 10 (n) korda
    * top -b -d 5 > logifail kirjutab käsu top tulemuse iga 5 sekundi tagant faili nimega logifail
    *     https://unix.stackexchange.com/questions/128953/how-to-display-top-results-sorted-by-memory-usage-in-real-time
*  **htop** - võimaldab kasutada hiirt ja lisab muid mugavusi.
*  **free** - Informatsioon vaba ja kasutatud mälu kohta
*  **vmstat** - saalimine ja katkestus
    * procs – väljastab protsesside arvu, mis on tööks valmis ja ootavad oma korda
    * memory – mälukasutus (swpd, saalemälu kasutuses, cache – puhvriteks kasutatava mälu hulk, mida saab vajadusel vabastada)
    * swap – si ja so näitavad, kui palju kirjutatakse ja loetakse kettalt saalemälu
    * io – bi, bo – sekundis väljundseadmetele kirjutatud ja loetud plokkide arv
    * sys – siin in – katkestuste arv, cs – kontekstivahetuste arv
    * cpu – protsessori kasutus (tähistus traditsiooniline: us - user, sy - system, wa - I/O wait, id - idle jne)
    * df näitab failisüsteemide vabu ressursse, näiteks:
      *  df -h väljastab info inimloetavas vormis (kasutades mega- ja kilobaite)
      *  df -i näitab kasutatud ja kasutada olevate i-kirjete (inode) arvu
    * du näitab kaustade ja failide kasutatud kettamahtu
      *  sudo du -h --max-depth=1
      *  du -s /*
      *  du -a / | sort -n -r | head -n 5
    *  **cat /proc/vmstat** - tuuma (kernel) poolt näidatavaid andme
*  mount
*  netstat
*  lsof

|Linux   | Windows  |
|---|---|
|ps	   | Task Manager  |
| pstree	| Process Explorer |
| top	| Task Manager / Process Explorer |
| free |	Task Manager, Performance tab |
| mount, df	| My Computer, Disk Manager |
| vmstat |	Resource Monitor |

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

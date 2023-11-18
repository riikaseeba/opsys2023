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
| Mitu protsessi kokku arvutis käib?  | 210  | 145  | ( ps -aux \| wc -l ) | Tegumihaldur -> jõudlus -> protsessid |
| Milline on kõige esimesena käivitatud protsess?  | /sbin/init splash   | smss.exe | ps axo pid,cmd,comm,etime  |  Process Explorer -> Start Time |
| Milliste kasutajate protsesse arvutis käib?   | USER, avahi, colord, kernoops, message+, riika, root, rtkit, syslog, systemd+  | Tavakasutajad (Riika)  | ps aux --sort=user \| awk '!seen[$1]++ {print $1}'  | Tegumihaldur -> kasutajad  |
| Kui kaua on arvuti järjest töötanud? |16:57:57 up 3 min   |  0:01:00:29 | w  |Tegumihaldud -> jõudlus -> tööaeg |
|  Milline protsess käivitati kõige hiljem? | /sbin/init splash  | svchost.exe  |ps -ef   | Process Explorer -> Start Time  |
| Milline on kõige rohkem protsessoriaega võttev protsess?  | /usr/bin/gnome-shell  | System Idle Process  | ps aux --sort -%cpu  | Process Explorer -> CPU  |
| Milline on kõige rohkem virtuaalmälu  võttev protsess? | /usr/bin/gnome-shell  | Windows Feature Experience Pack  |ps -aux --sort -vsz   | Tegumihaldur -> rakenduse ajalugu  |
| Milline on kõige rohkem füüsilist mälu võttev protsess?  | /usr/bin/gnome-shell  | Antimalware Service Executable  |ps -aux --sort -rss  | Tegumihaldur -> mälu  |
|  Kui palju füüsilisest mälust on vaba? | 74884 K free memory  | 1,8GB  | vmstat -s  | Tegumihaldur -> jõudlus -> mälu -> saadaval  |
|  Kui palju on põhikettal (C:, /) vaba ruumi mahult (GB) ja protsentuaalselt? | 11GB ehk 52%  | 26,8GB ehk  42% | df --block-size 1G  | File Explorer -> See arvuti -> vaba maht (või parem hiirklahv -> atribuudid -> maht) |
| Milline on kõige suurem kõvakettal olev fail ja kõige suurem alamkaust?  | alamkataloog: /usr, fail: /proc/kcore  | Alamkaust: Windows, Fail: Pagefile.sys | alamkaust: sudo du -k -d1 /, fail: sudo find / -type f -printf "%s\t%p\n" \| sort -n \| tail -1  | Alamkaust: Windirstat.exe -> Suurus (Suurem->väiksem), Fail: Windirstat.exe -> Leidsin graafikult suurima kasti ja leidsin vastava faili nime |

## küsimused 12-15
### 12. (ainult Linuxis)

sha1sum /dev/zero | sha1sum /dev/zero - puhul us'ile kulub enim protsessori aega (kõigub 93 ja 97 % vahel)

<img width="589" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/78199439-5dec-4b9e-b39f-64d41b1aa504">

sha1sum /dev/urandom | sha1sum /dev/urandom - puhul sy'le kulub enim protsessori aega (60% ümbruses)

<img width="536" alt="image" src="https://github.com/riikaseeba/opsys2023/assets/144622934/bdfee96f-0abd-49f2-8ba4-137c77272d6e">


### 13. (Ainult Windowsis)
|Küsimus   | vastus  | Kust vastuse sain  |
|---|---|---|
| Milline protsess kõige rohkem salvestusseadmele kirjutab?  | System  | (Task Manager -> Resource monitor -> Disk -> Write (Sort suurem->väiksem))  | 
|   Millisesse faili eelmise küsimuse protsess kõige rohkem kirjutab?  |   |   | 
| Milline protsess kõige rohkem salvestusseadmelt loeb?  | svchost.exe  | (Task Manager -> Resource monitor -> Disk -> Read (Sort suurem->väiksem))  | 
| Millisest failist eelmise küsimuse protsess kõige rohkem loeb?  |   |   |
        

### 14. Millise protsessi poolt tekitatud võrguliiklus on suurima mahuga? (Ainult Windowsis)
|Küsimus   | vastus  | Kust vastuse sain  |
|---|---|---|
| Millise protsessi poolt tekitatud võrguliiklus on suurima mahuga?   |svchost.exe   | (Networkservice -p), Local IP: 10.0.2.15, Local Port: 50101, Remote IP: 192.168.1.191, Remote Port: 7680, Latency: -  |

![image](https://github.com/riikaseeba/opsys2023/assets/144622934/920e5599-8e7d-40c7-9929-9059149f431f)


### 15. (Windowsis)
   *   Kõige parem programm on Task Manager, kus saab jälgida protsessori ja mälu kasutust, ketta aktiivsusaega, võrgukasutust ning graafikakaardi kasutust. Neid andmeid saab sorteerida (Suurem kasutus -> väiksem kasutus). Kui arvuti on aeglane siis tuleks jälgida protsessori, mälu ja kettakasutuse andmeid. Kui need on ligidal 100% kasutusele siis tuleks vaadata sorteerimise abil, milline programm antud ressurssi kõige rohkem kasutab ja võimalusel see kinni panna. Kui tegemist on kriitilise protsessiga, mida ei saa kinni panna, siis on juba piirav faktor riistvara, mida käsurea vms kiiremaks muuta ei saa (v.a ülekiirendamine, mis annab marginaalse "boosti")
